# DataBase Dictionary Web page Generator.

HtmlDict is a v8+ compatible metaschema web page creator. These programs allow you to map some or all connected databases into a 
series of web pages. The top page shows all processed databases, the next level shows all tables within a database, and the last level 
shows all fields within a table. All table pages are linked to the Next and Previous page, and back to the level above. Additionally, 
a field cross index, a sequence list and an area overview is generated and linked in to the database and table pages. 

This set of pages is an easy way to see all the fields, tables, and databases with all relevant details for coding, without 
switching to the data dictionary.

HtmlDict is based on the updated version from 3 oct 2002 from Jeff Pilant, which, in turn, was based on the original version from 
Tom Bascom, dated 11 jan 1996. Many thanks go to these guys for the basic idea.

## Screenshot
![HtmlDict screenshot](https://github.com/patrickTingen/HtmlDict/blob/main/screenshot.png "HtmlDict Screenshot")

## How to install:

Extract the contents of the zipfile to a dir. Keep path names as defined in the zip, so you should end up with a directory containing some files and one directory called "static"


## How to run:

Open your editor, and run "launch.p" with a fully specified path. If you installed HtmlDict to
D:\data\progress\htmldict then you should use:
```
RUN D:\data\progress\htmldict\launch.p
```


## Results

In the main directory the following files are created:

|File              |Description                            |
|----------------  |---------------------------------------|
|00-index.html     |Main entry point for the list of db's. |
|HtmlDict.html     |Page with version info.                |
|HtmlDict.ico      |Icon file for the webpages             |
|styles.css        |Cascaded style sheet for the database. |

Then, a subfolder is created for each database it processes, holding the generated .html files and these extra files:

|File              |Description                                                                                                   |
|----------------  |------------------------------------------------|
|00-area.html      |overview of the areas of the database           |
|00-cross.html     |cross-index of the fieldnames in the db.        |
|00-index.html     |frameset                                        |
|00-list.html      |list of file names (left frame)                 |
|00-main.html      |main page with a list of the files              |
|00-crc.txt        |list of crc's for all the files in the database |
|00-primeindex.txt |list with all single-field primary indexes.     |

Your entry point to the generated pages is *HtmlDict.html* in the main folder. 


## Autostart

You can run htmldict automatically. For this, you need to create a shortcut to HtmlDict.w and provide the options you want in the -param string. Possible options are:

|Option              |Description                                                 |Values
|-----------------   |---------------------------------------------------------   |------------------------  |
|x                   |x-position of the window                                    |valid position            |
|y                   |y-position of the window                                    |valid position            |
|FieldOrder          |sort order for the fields                                   |'_order' | '_field-name'  |
|SkipIfUnchanged     |do not generate the HTML pages is the schema is unchanged   |TRUE|FALSE                |
|ShowHtml            |show the startpage after the generating process             |TRUE|FALSE                |
|SaveSettings        |save the settings in the registry                           |TRUE|FALSE                |
|OutputDirectory     |directory where the HTML pages will be saved.               |valid directory           |
|TriggerPath         |directory where the trigger code can be found               |list of valid directories |
|AutoRun             |automatic run and quit                                      |TRUE|FALSE                |

The settings can be specified inside the -param string, separated with spaces. A valid startup string would be: 
  -param "SaveSettings=false x=10 y=10 SkipIfUnchanged=true AutoRun=true"

Command line settings overrule the settings from the registry. Unless you specify 'SaveSettings=false', the 
settings you specify on the commandline might be saved to the registry (depending on your last run). You cannot 
specify the databases to be processed. By default, all connected databases and the metaschema will be processed, so 
connect your databases using -db on the command line. If you use the autorun feature, you might want to add -rr to 
the startup parameters to make Progress think it is running in a run-time environment. 

