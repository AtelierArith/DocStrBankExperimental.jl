```
setall(obj, optic, values)
```

Replace a part of `obj` that is selected by `optic` with `values`. The `values` collection should have the same number of elements as selected by `optic`.

The details of `setall` behavior are consireded experimental: in particular, supported container types for the `values` argument might change in the future.

See also [`getall`](@ref), [`set`](@ref). The former is dual to `setall`:

```jldoctest
julia> using Accessors

julia> obj = (a=1, b=(2, 3));

julia> optic = @optic _ |> Elements() |> last;

julia> getall(obj, optic)
(1, 3)

julia> setall(obj, optic, (4, 5))
(a = 4, b = (2, 5))
```
