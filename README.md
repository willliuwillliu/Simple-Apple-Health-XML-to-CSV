# Simple Apple Health XML to CSV - Workouts only fork

A simple script to convert Apple Health's export.xml file to an easy to use csv.

This is a fork of (jameno/Simple-Apple-Health-XML-to-CSV)[https://github.com/jameno/Simple-Apple-Health-XML-to-CSV]. The original code worked fine but the export was still too huge (mine was 2M rows).

This fork transforms the XML into CSV but also does the following:

- Filters for only workouts
- Renames removes "HKWorkoutActivityType" from the values in `workoutActivityType`
- Removes empty columns

## How to Run

### 1. Verify you have Python 3 & Pandas installed on your machine or environment

`python --version` should return _Python 3.x.x_ where x is any number.

If you have Python 2.x.x, please upgrade to Python 3 here: https://www.python.org/downloads/ (or specify your environment's Python version)

`python3 -c "import pandas"` should return blank from the command line

If you get a _**ModuleNotFoundError: No module named 'pandas'**_ error, install pandas and try again:

`pip3 install pandas`

### 2. Export your Apple Health Data

Go to your health home screen and click on the profile icon

<img style="float: left;" src="img/health_home.jpg" width=300>

On the next page, click the "Export Health Data" button

<img style="float: left;" src="img/export_data_button.jpg" width = 300 >

Your data will be prepared, and then you can transfer the export.zip file to your machine.

### 3. Unzip the file, which should contain:

- apple_health_export

  - export.xml

  - export_cda.xml

### 4. Place the "apple_health_xml_convert.py" file from this repo into the folder alongside the files and run the script

`python3 apple_health_xml_convert.py`

The export will be written with the format:

- **apple_health_export_YYYY-MM-DD.csv**

In Excel, the output should look something like this:

<img style="float: left;" src="img/example_output.jpg">

Note: This script removes the Apple Health data prefixes: `HKQuantityTypeIdentifier`, `HKCategoryTypeIdentifier`, and `HKCharacteristicTypeIdentifier` for increased legibility. Feel free to comment out those lines in the code with a `#` if you want to keep them in the CSV output.
