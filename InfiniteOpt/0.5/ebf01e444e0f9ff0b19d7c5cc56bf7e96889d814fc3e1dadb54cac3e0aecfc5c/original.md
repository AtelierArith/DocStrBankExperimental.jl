```
set_infinite_domain(pref::IndependentParameterRef,
                 domain::InfiniteScalarDomain)::Nothing
```

Reset the infinite domain of `pref` with another `InfiniteScalarDomain`. An error will  be thrown if `pref` is being used by some measure.

**Example**

```julia-repl
julia> set_infinite_domain(t, IntervalDomain(0, 2))

julia> infinite_domain(t)
[0, 2]
```
