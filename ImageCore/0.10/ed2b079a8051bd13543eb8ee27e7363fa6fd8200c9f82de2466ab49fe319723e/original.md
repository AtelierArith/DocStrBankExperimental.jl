```
namedaxes(img) -> NamedTuple{names}(axes)
```

Returns a `NamedTuple` where the names are the dimension names and each indice is the corresponding dimensions's axis. If `HasDimNames` is not defined for `x` default names are returned. `x` should have an `axes` method.

```jldoctest; setup = :(using ImageCore)
julia> img = reshape(1:24, 2,3,4);

julia> namedaxes(img)
(dim_1 = Base.OneTo(2), dim_2 = Base.OneTo(3), dim_3 = Base.OneTo(4))
```
