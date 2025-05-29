```
Index[i]
```

This exists to let you mix in square-bracket indexing, like `A(:b, Near(3.14), Index[4:5], "f")`. You may also write `Index[end]`, although not yet `Index[end-2]`.

```
Key(val)
```

This exists to perform lookup inside indexing, to allow `A[Key(:b), Near(3.14), 4:5, Key("f")]`.

Writing `Key(isequal(:b))` is equivalent to just `isequal(:b)`, and will find all matches, while `Key(:b)` finds only the first (and drops the dimension).

# Examples

```jldoctest
julia> v = KeyedArray(Symbol.('a':'e'), 10:10:50)
1-dimensional KeyedArray(...) with keys:
↓   5-element StepRange{Int64,...}
And data, 5-element Vector{Symbol}:
 (10)  :a
 (20)  :b
 (30)  :c
 (40)  :d
 (50)  :e

julia> v[Key(30)] == v(30) == v(Index[3]) == v[3]
true

julia> v[==(30)] == v(Index[3:3]) == v[3:3]
true
```
