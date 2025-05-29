```
partition(xs, n, [step])
```

Group values into `n`-tuples.

```jldoctest
julia> for i in partition(1:9, 3)
           @show i
       end
i = (1, 2, 3)
i = (4, 5, 6)
i = (7, 8, 9)
```

If the `step` parameter is set, each tuple is separated by `step` values.

```jldoctest
julia> for i in partition(1:9, 3, 2)
           @show i
       end
i = (1, 2, 3)
i = (3, 4, 5)
i = (5, 6, 7)
i = (7, 8, 9)

julia> for i in partition(1:9, 3, 3)
           @show i
       end
i = (1, 2, 3)
i = (4, 5, 6)
i = (7, 8, 9)

julia> for i in partition(1:9, 2, 3)
           @show i
       end
i = (1, 2)
i = (4, 5)
i = (7, 8)
```
