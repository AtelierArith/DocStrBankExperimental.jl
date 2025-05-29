```
q_translate(h::String; sp = false)
```

Convert a string `h` representing multi-qubits Pauli matrices summation into its numerical form. Generate sparse matrix when `sp` is set to true.

# Examples

```julia-repl
julia> q_translate("X+2.0Z")
2×2 Array{Complex{Float64},2}:
 2.0+0.0im   1.0+0.0im
 1.0+0.0im  -2.0+0.0im
```
