```
xticks(sp::Subplot)
```

returns the x-axis ticks of the subplot `sp`.

Note that the ticks are returned as tuples of values and labels:

```jldoctest
julia> sp = plot(1:5, xticks=[1,2]).subplots[1]
Subplot{1}

julia> xticks(sp)
([1.0, 2.0], ["1", "2"])
```
