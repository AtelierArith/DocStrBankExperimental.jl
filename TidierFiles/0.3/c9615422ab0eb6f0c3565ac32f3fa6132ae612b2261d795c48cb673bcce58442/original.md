```
list_files(path = "", pattern = "")
```

List all files in a directory that match a given pattern.

# Arguments

  * `path`: The directory path to list files from. Defaults to an empty string.
  * `pattern`: A string pattern to filter the files. Defaults to an empty string, matching all files. ie `.csv` will only return files ending in .csv

# Examples

  * `list_files("/path/to/folder/", ".csv")`
