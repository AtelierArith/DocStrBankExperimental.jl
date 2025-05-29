```
getall(obj, optic)
```

Extract all parts of `obj` that are selected by `optic`. Returns a flat `Tuple` of values, or an `AbstractVector` if the selected parts contain arrays.

The details of `getall` behavior are consireded experimental: in particular, the precise output container type might change in the future.

See also [`setall`](@ref).

```jldoctest
julia> using Accessors

julia> obj = (a=1, b=(2, 3));

julia> getall(obj, @optic _.a)
(1,)

julia> getall(obj, @optic _ |> Elements() |> last)
(1, 3)
```
