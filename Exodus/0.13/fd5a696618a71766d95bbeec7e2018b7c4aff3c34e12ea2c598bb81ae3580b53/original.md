```julia
ExodusDatabase(
    file_name::String,
    mode::String
) -> Exodus.ExodusDatabase{_A, _B, _C, _D, Exodus.Initialization{ND, NN, NE, NEB, NNS, NSS}} where {_A, _B, _C, _D, ND, NN, NE, NEB, NNS, NSS}

```

Type unstable helper to eliminate annoying lines of code to get type stability.

If you're looking for a type stable way to to open an exodus file, Simple copy past some of this into a barrier function
