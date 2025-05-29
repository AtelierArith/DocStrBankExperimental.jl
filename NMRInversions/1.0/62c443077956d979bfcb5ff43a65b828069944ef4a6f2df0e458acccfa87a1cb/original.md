```
import_spinsolve(files)
```

Import data from a Spinsolve experiment.  Two paths must be provided as follows (order is not important):

  * `files` = [.../datafile.csv , .../acqu.par]

Calling this function without an argument by typing `import_spinsolve()` will open a file dialog to select the files. The function reads the acqu.par.bak file to get the acquisition parameters, and the .dat file to get the data.  The function returns an `input2D` structure.
