```
nth(xs, n)
```

Return the `n`th element of `xs`. This is mostly useful for non-indexable collections.

```jldoctest
julia> powers_of_two = iterated(x->2x,1);

julia> nth(powers_of_two, 4)
8
```
