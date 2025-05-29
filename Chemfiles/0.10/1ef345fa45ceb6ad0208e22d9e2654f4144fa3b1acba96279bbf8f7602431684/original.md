```julia
matrix(cell::Chemfiles.UnitCell) -> Matrix{Float64}

```

Get the `cell` matricial representation, *i.e.* the representation of the three base vectors as:

```
    | a_x   b_x   c_x |
    |  0    b_y   c_y |
    |  0     0    c_z |
```
