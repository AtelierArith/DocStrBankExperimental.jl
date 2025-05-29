```
gibbs_state(h, β)
```

Calculate the Gibbs state of the matrix `h` at temperature `T` (mK).

# Examples

```julia-repl
julia> gibbs_state(σz, 10)
2×2 Array{Complex{Float64},2}:
 0.178338+0.0im       0.0+0.0im
      0.0+0.0im  0.821662+0.0im
```
