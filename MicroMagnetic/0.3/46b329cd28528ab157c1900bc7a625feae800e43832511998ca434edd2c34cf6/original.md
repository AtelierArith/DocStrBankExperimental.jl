```
read_table(filename::String)
```

Reads a data table from the specified file `filename`. The file should contain comment lines starting with `#`, where the first comment line  includes the physical quantity names and the second comment line includes the units. The data starts from the `start_idx` line, which is the first line of actual data.

### Parameters

  * `filename::String` : Path to the data file.

### Returns

  * Two dictionaries:

      * `data` : A dictionary where keys are the physical quantity names and values are vectors of corresponding floating-point data.
      * `units` : A dictionary where keys are the physical quantity names and values are the corresponding unit strings.

### Example

```julia data, units = read_table("data.txt")
