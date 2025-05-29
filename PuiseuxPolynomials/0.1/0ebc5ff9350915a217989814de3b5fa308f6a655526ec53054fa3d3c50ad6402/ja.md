`variables(p::Mvp)`

`variables(v::AbstractArray)`

`p`（または`v`内のすべての`p`）の変数のリストを`Symbol`のソートされたリストとして返します。

```julia-repl
julia> @Mvp x,y,z

julia> variables([z,[y+z],x])
3-element Vector{Symbol}:
 :x
 :y
 :z
```
