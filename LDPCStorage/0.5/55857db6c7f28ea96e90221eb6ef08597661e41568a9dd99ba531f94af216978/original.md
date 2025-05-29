```julia
print_cpp_header_QC(io, H; expansion_factor, namespace_name)

```

Output C++ header storing the quasi-cyclic exponents of an LDPC matrix in compressed sparse column (CSC) format. This implies three arrays, which are called `colptr`, `row_idx` and `values`. The expansion factor must also be given (it is simply stored as a variable in the header).

Note the conversion from Julia's one-based indices to zero-based indices in C++ (also within CSC format)!
