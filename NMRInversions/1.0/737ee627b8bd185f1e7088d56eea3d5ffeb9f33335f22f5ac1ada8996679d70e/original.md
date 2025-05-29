```
import_csv(seq, file)
```

Import data from a CSV file. The function reads the file and returns an `input1D` structure.

  * `seq` is the 1D pulse sequence (e.g. IR, CPMG, PFG)
  * `file` is the path to the CSV file which contains the data (x, y) in two respective columns.

The function can be called without the seq argument, and the output will be the x and y vectors  (use it like, `x,y =import_csv()`). Alternatively, the function can also be called with only the seq argument, in which case a file dialog will open to select the file (use it like, `data = import_csv(IR)`)

Please note that this function will just import the data as is, without any unit conversions. Ensure that your x-axis is in SI.
