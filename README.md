# utl_given_meta_data_with_mutiple_filepaths_and_accounts_create_an_xml_file_for_each_filepath_and_acc
Given meta data with mutiple filepaths and accounts create an xml file for each filepath and account.  Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.
    SAS Forum: Given meta data with mutiple filepaths and accounts create an xml file for each filepath and account

    github
    https://tinyurl.com/y8duaeyb
    https://github.com/rogerjdeangelis/utl_given_meta_data_with_mutiple_filepaths_and_accounts_create_an_xml_file_for_each_filepath_and_

    SAS Forum
    https://tinyurl.com/yap76ewp
    https://communities.sas.com/t5/Base-SAS-Programming/read-variables-from-dataset-and-pass-it-to-a-macro/m-p/446181


    INPUT
    =====

     WORK.ACCOUNTS total obs=2

      ACCOUNTNUMBER      FILESTRING

           1234        d:\xml\1234.xml
           5678        d:\xml\5678.xml


      EXAMPLE OUTPUT  (Two xml files with account information)

        d:\xml\5678.xml
          <accountID>1234</accountID>

        d:\xml\5678.xml
          <accountID>5678</accountID>


    PROCESS (all the code)
    ======================

    data _null_;

      set accounts;  * cycle through meta data;

       accountString = put (accountNumber, 4.);

       * pass this data to dosubl subroutine;
       call symputx('accountString',accountString);
       call symputx('fileString',fileString);

       * you can use a macro but this seems more clear;
       rc=dosubl('
          data _null_;
          file "&fileString";
          put "<accountID>" "&accountString" "</accountID>";
          run;quit;
       ');

    run;quit;


    OUTPUT
    ======

      Two xml files with account information)

        d:\xml\5678.xml
          <accountID>1234</accountID>

        d:\xml\5678.xml
          <accountID>5678</accountID>

    *                _               _       _
     _ __ ___   __ _| | _____     __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|

    ;

    DATA accounts;
        INPUT accountNumber BEST4. fileString $ CHAR16.;
    DATALINES4;
    1234 d:\xml\1234.xml
    5678 d:\xml\5678.xml
    ;;;;
    run;quit;


    *          _       _   _
     ___  ___ | |_   _| |_(_) ___  _ __
    / __|/ _ \| | | | | __| |/ _ \| '_ \
    \__ \ (_) | | |_| | |_| | (_) | | | |
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|

    ;


    data _null_;

      set accounts;  * cycle through meta data;

       accountString = put (accountNumber, 4.);

       * pass this data to dosubl subroutine;
       call symputx('accountString',accountString);
       call symputx('fileString',fileString);

       * you can use a macro but this seems more clear;
       rc=dosubl('
          data _null_;
          file "&fileString";
          put "<accountID>" "&accountString" "</accountID>";
          run;quit;
       ');

    run;quit;


    SYMBOLGEN:  Macro variable FILESTRING resolves to d:\xml\1234.xml
    SYMBOLGEN:  Macro variable ACCOUNTSTRING resolves to 1234
    NOTE: The file "d:\xml\1234.xml" is:
          Filename=d:\xml\1234.xml,
          RECFM=V,LRECL=384,File Size (bytes)=0,
          Last Modified=16Mar2018:11:34:36,
          Create Time=16Mar2018:11:21:48

    NOTE: 1 record was written to the file "d:\xml\1234.xml".
          The minimum record length was 27.
          The maximum record length was 27.
    NOTE: DATA statement used (Total process time):
          real time           0.01 seconds
          cpu time            0.01 seconds


    SYMBOLGEN:  Macro variable FILESTRING resolves to d:\xml\5678.xml
    SYMBOLGEN:  Macro variable ACCOUNTSTRING resolves to 5678
    NOTE: The file "d:\xml\5678.xml" is:
          Filename=d:\xml\5678.xml,
          RECFM=V,LRECL=384,File Size (bytes)=0,
          Last Modified=16Mar2018:11:34:37,
          Create Time=16Mar2018:11:21:49

    NOTE: 1 record was written to the file "d:\xml\5678.xml".
          The minimum record length was 27.
          The maximum record length was 27.
    NOTE: DATA statement used (Total process time):
          real time           0.03 seconds
          cpu time            0.01 seconds


    NOTE: There were 2 observations read from the data set WORK.ACCOUNTS.
    NOTE: DATA statement used (Total process time):
          real time           1.36 seconds
          cpu time            0.57 seconds

    275 !     quit;



