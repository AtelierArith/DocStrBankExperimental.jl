```
nitems(xs) -> n::Integer
```

Count number of items in `xs`.  Consume `xs` if necessary.

# Examples

```jldoctest
julia> using DataTools, Transducers

julia> nitems(1:10)
10

julia> 1:10 |> Filter(isodd) |> Map(inv) |> nitems
5
```
