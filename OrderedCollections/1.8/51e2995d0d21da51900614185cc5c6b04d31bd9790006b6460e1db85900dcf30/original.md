```
OrderedSet
```

`OrderedSet`s are simply sets whose entries have a particular order. The order refers to insertion order, which allows deterministic iteration over the set.

Note: To create an OrderedSet of a particular type, you must specify the type, such as,

```julia
os = OrderedSet{Int}(3)
push!(os, [1,2]...)
```
