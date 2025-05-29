```
droplevels!(A::CategoricalArray)
```

Drop levels which do not appear in categorical array `A` (so that they will no longer be returned by [`levels`](@ref DataAPI.levels)).
