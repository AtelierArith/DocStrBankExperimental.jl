```
densityof(object)
```

Return a function that computes the value of the density `object` (resp. its associated density) at a given point.

```jldoctest a
julia> f = densityof(object);

julia> f(x) == densityof(object, x)
true
```

`densityof(object)` defaults to `Base.Fix1(densityof, object)`, but may be specialized.
