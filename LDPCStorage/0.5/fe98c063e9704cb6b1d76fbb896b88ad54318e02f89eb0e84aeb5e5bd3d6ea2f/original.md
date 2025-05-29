```julia
print_cpp_header(io, H; namespace_name)

```

Output C++ header storing the sparse binary (containing only zeros and ones) matrix H in compressed sparse column (CSC) format.

Note the conversion from Julia's one-based indices to zero-based indices in C++ (also within CSC format)!
