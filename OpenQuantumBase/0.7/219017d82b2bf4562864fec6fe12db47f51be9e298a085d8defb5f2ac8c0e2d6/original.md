```julia
matrix_decompose(mat, basis)

```

Decompse matrix `mat` onto matrix basis `basis`

# Examples

```julia-repl
julia> matrix_decompose(1.0*σx+2.0*σy+3.0*σz, [σx,σy,σz])
3-element Array{Complex{Float64},1}:
 1.0 + 0.0im
 2.0 + 0.0im
 3.0 + 0.0im
```
