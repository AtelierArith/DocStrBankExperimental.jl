```
write_win(filename, params; header)
write_win(filename, params, ::Wannier90Text; header)
write_win(filename, params, ::Wannier90Toml; header)
write_win(filename; header, params...)
write_win(filename, ::Wannier90Text; header, params...)
write_win(filename, ::Wannier90Toml; header, params...)
```

Write input parameters into a wannier90 `win` file.

There are two choice for passing the input parameters:

1. as a `Dict` (or `OrderedDict` to preserve ordering) to the `params` argument
2. as keyword arguments `params...`, with argument names the same as the input  parameters of wannier90

# Examples

```julia
using WannierIO

# you can also use `Dict` or `OrderedDict`
params = (;
    num_wann=4,
    num_bands=4,
    # unit_cell_cart is a matrix, its columns are the lattice vectors in angstrom
    unit_cell_cart=[
        0.0      2.71527  2.71527
        2.71527  0.0      2.71527
        2.71527  2.71527  0.0
    ],
    # atoms_frac is a vector of pairs of atom_label and fractional coordinates
    atoms_frac=[
        :Si => [0.0, 0.0, 0.0],
        :Si => [0.25, 0.25, 0.25],
        # both `:Si` and `"Si"` are allowed
        # "Si" => [0.25, 0.25, 0.25],
    ],
    # each element in projections will be written as a line in the win file
    projections=[
        "random",
    ]
    kpoint_path=[
        [:G => [0.0, 0.0, 0.0], :X => [0.5, 0.0, 0.5]],
        [:X => [0.5, 0.0, 0.5], :U => [0.625, 0.25, 0.625]],
    ],
    mp_grid=[2, 2, 2],
    # kpoints is a matrix, its columns are the fractional coordinates
    kpoints=[
        [0.0, 0.0, 0.0],
        [0.0, 0.0, 0.5],
        [0.0, 0.5, 0.0],
        [0.0, 0.5, 0.5],
        [0.5, 0.0, 0.0],
        [0.5, 0.0, 0.5],
        [0.5, 0.5, 0.0],
        [0.5, 0.5, 0.5],
    ],
    # additional parameters can be passed as keyword arguments, e.g.,
    num_iter=500,
)
write_win("silicon.win", params)
```
