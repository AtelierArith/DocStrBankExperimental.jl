```julia
print_bincscjson(io, mat; comments)

```

Writes the two arrays `colptr` and `rowval` defining compressed sparse column (CSC) storage of a the into a json file. Errors unless sparse matrix only contains ones and zeros. The third array of CSC format, i.e., the nonzero entries, is not needed, since the matrix is assumed to only contain ones and zeros.
