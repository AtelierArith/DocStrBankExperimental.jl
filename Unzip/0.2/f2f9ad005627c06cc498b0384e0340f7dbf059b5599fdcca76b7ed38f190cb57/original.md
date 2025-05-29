```
unzip(rows)
```

Collect into columns.

Will be most performant if each row is a tuple. If each row is not a tuple, consider using `unzip(Iterators.map(Tuple, rows))`.

```jldoctest
julia> using Unzip

julia> using Test: @inferred

julia> stable(x) = (x, x + 0.0, x, x + 0.0, x, x + 0.0);

julia> @inferred unzip(Iterators.map(stable, 1:4))
([1, 2, 3, 4], [1.0, 2.0, 3.0, 4.0], [1, 2, 3, 4], [1.0, 2.0, 3.0, 4.0], [1, 2, 3, 4], [1.0, 2.0, 3.0, 4.0])

julia> unstable(x) =
           if x == 2
               (x, x + 0.0, x, x + 0.0)
           else
               (x, x + 0.0)
           end;

julia> unzip(Iterators.map(unstable, 1:3))
([1, 2, 3], [1.0, 2.0, 3.0], Union{Missing, Int64}[missing, 2, missing], Union{Missing, Float64}[missing, 2.0, missing])
```
