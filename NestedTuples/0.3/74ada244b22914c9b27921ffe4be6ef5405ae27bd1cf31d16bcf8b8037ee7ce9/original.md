```
randnt(width::Int, depth::Int)
```

Construct a random nested NamedTuple with `Symbol`s at the leaves, width `width`, and depth `depth`

EXAMPLE:

```
julia> randnt(3,2)
(a = (y = :y, r = :r, p = :p), v = (f = :f, e = :e, v = :v))
```
