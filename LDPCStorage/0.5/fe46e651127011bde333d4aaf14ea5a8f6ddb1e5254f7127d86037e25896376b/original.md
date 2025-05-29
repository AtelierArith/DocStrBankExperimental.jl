```julia
print_qccscjson(io, mat; qc_expansion_factor, comments)

```

write the three arrays defining compressed sparse column (CSC) storage of a matrix into a file. This is used to store the exponents of a quasi-cyclic LDPC matrix. The matrix is assumed to contain quasi-cyclic exponents of an LDPC matrix. The QC expansion factor must be specified.
