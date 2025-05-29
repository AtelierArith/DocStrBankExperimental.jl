```
makecrys(A,coords,types; units=missing)
```

Return a crystal object from 3×3 lattice, nat × 3 coords in crystal units, and nat element strings.

Will use units set by `set_units`, with default to Ang. Can override with `units`.

Note: also export-ed directly from ThreeBodyTB for convenience

```julia-repl
julia> makecrys([10.0 0 0; 0 10.0 0; 0 0 10.0], [0.0 0.0 0.0], ["H"])
A1=     10.00000  0.00000  0.00000
A2=     0.00000  10.00000  0.00000
A3=     0.00000  0.00000  10.00000

H    0.00000  0.00000  0.00000
```
