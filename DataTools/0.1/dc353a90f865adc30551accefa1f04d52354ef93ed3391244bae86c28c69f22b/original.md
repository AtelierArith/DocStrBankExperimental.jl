```
firstitem(xs)
```

Get the first item of `xs`.  Consume `xs` if necessary.

# Examples

```jldoctest
julia> using DataTools, Transducers

julia> firstitem(3:7)
3

julia> 3:7 |> Map(x -> x + 1) |> Filter(isodd) |> firstitem
5
```
