```
free_symbols(ex)
free_symbols(ex::Vector{Sym})
```

Return vector of free symbols of expression or vector of expressions. The results are orderded by `sortperm(string.(fs))`.

Example:

```jldoctest
julia> using SymPyPythonCall

julia> @syms x y z a
(x, y, z, a)

julia> free_symbols(2*x + a*y) # [a, x, y]
3-element Vector{Sym{PythonCall.Py}}:
 a
 x
 y


julia> free_symbols([x^2, x^2 - 2x*y + y^2])
2-element Vector{Sym{PythonCall.Py}}:
 x
 y
```
