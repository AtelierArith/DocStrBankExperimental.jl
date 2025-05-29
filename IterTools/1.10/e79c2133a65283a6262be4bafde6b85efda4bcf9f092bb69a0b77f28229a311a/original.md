```
zip_longest(iters...; default=nothing)
```

For one or more iterable objects, return an iterable of tuples, where the `i`th tuple contains the `i`th component of each input iterable if it is not finished, and `default` otherwise. `default` can be a scalar, or a tuple with one default per iterable.

```jldoctest
julia> for t in zip_longest(1:2, 5:8)
         @show t
       end
t = (1, 5)
t = (2, 6)
t = (nothing, 7)
t = (nothing, 8)

julia> for t in zip_longest('a':'e', ['m', 'n']; default='x')
         @show t
       end
t = ('a', 'm')
t = ('b', 'n')
t = ('c', 'x')
t = ('d', 'x')
t = ('e', 'x')
```
