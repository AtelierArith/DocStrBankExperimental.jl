```julia
save_to_bincscjson(destination_file_path, mat; varargs...)

```

Helper method to use with files. See `print_bincscjson` for main interface.

Writes the two arrays `colptr` and `rowval` defining compressed sparse column (CSC) storage of a the into a json file. Errors unless sparse matrix only contains ones and zeros. The third array of CSC format, i.e., the nonzero entries, is not needed, since the matrix is assumed to only contain ones and zeros.
