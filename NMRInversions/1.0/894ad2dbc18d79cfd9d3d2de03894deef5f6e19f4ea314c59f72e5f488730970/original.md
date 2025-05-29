```
import_geospec(dir)
```

Import data from a .txt format, as exported by Geospec instruments.

The function reads the relevant information, performs a phase correction on the data, and returns an `input1D` or `input2D` structure.

Calling this function without an argument by typing `import_geospec()`  will open a file dialog to select the .txt file.
