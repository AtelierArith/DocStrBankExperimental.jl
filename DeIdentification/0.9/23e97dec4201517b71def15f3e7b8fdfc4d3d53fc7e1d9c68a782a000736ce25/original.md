```
build_config_from_csv(project_name::String, file::String)
```

Generates a configuration YAML file from a CSV file that defines the mappings. The CSV file needs to have at least three named columns, one called **Source Table** which defines the name of the CSV file the data will be read from, a second called **Field** which defines the name of the field in the data source and a final column called **Method** which contains the method to apply (one of **Hash - Research ID**, **Hash**, **Hash & Salt**, **Date Shift**, or **Drop**).

Any column renames and pre- or post-processing will need to be added manually to the file.
