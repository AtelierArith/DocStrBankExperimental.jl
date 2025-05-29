```
compose(a::Vector{Range}, b::Vector{Range}) -> Vector{Range}
```

`a`を適用した後に`b`を適用することに相当する変更のセットを返します。

```julia
Pinot.apply(Pinot.apply(text, a), b) ==
    Pinot.apply(text, Pinot.compose(a, b))
```
