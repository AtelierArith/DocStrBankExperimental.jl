```julia
ExodusPostProcessor(
    mesh_file::String,
    output_file::String,
    solution_fields::Vector{String}
) -> Cthonios.ExodusPostProcessor{Exo} where Exo<:(Exodus.ExodusDatabase{_A, _B, _C, _D, Exodus.Initialization{ND, NN, NE, NEB, NNS, NSS}} where {_A, _B, _C, _D, ND, NN, NE, NEB, NNS, NSS})

```

Constructor for `ExodusPostProcessor`. `mesh_file` - A name of a mesh file to copy. `output_file` - A name of file to copy the mesh to. `solution_fields` - Names for the nodal solution fields.
