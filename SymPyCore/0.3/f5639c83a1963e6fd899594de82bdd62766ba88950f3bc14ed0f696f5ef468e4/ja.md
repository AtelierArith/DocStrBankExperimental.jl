```
free_symbols(ex)
free_symbols(ex::Vector{Sym})
```

式または式のベクトルの自由記号のベクトルを返します。結果は `sortperm(string.(fs))` によって順序付けられます。

例:

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
