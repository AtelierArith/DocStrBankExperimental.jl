```julia
save_to_qccscjson(destination_file_path, mat; varargs...)

```

Helper method to use with files. See `print_qccscjson` for main interface.

write the three arrays defining compressed sparse column (CSC) storage of a matrix into a file. This is used to store the exponents of a quasi-cyclic LDPC matrix. The QC expansion factor must be specified.
