```julia
ExodusDatabase(
    file_name::String,
    mode::String,
    init::Exodus.Initialization,
    _::Type{M},
    _::Type{I},
    _::Type{B},
    _::Type{F}
) -> Exodus.ExodusDatabase{_A, _B, _C, _D, Exodus.Initialization{ND, NN, NE, NEB, NNS, NSS}} where {_A, _B, _C, _D, ND, NN, NE, NEB, NNS, NSS}

```
