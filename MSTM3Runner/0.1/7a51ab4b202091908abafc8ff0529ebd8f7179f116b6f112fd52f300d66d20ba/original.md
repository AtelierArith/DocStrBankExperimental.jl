```julia
write_tmatrix(filename, 𝐓, shape)

```

Write the T-Matrix to `filename` in the format expected by MSTM3.

Note that in MSTM3, `TM = 1` and `TE = 2`, which is the opposite of the definition in `TransitionMatrices.jl`.
