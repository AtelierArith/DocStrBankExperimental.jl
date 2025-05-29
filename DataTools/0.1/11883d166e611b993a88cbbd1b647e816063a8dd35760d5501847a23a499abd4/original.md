```
lastitem(xs)
```

Get the last item of `xs`.  Consume `xs` if necessary.

# Examples

```jldoctest
julia> using DataTools, Transducers

julia> lastitem(3:7)
7

julia> 3:7 |> Map(x -> x + 1) |> Filter(isodd) |> lastitem
7
```
