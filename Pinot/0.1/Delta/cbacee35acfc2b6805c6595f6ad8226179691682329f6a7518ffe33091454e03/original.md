```
compose(a::Vector{Range}, b::Vector{Range}) -> Vector{Range}
```

Returns a set of changes equivalent to sequentially applying `a` then `b`.

```julia
Pinot.apply(Pinot.apply(text, a), b) ==
    Pinot.apply(text, Pinot.compose(a, b))
```
