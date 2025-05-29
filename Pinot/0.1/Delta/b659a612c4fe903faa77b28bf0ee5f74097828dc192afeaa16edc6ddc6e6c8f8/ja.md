```
transform(a::Vector{Range}, b::Vector{Range}, priority=Left) -> Vector{Range}
```

`a`に対して変換された`b`のバージョンを生成します：

```julia
Pinot.apply(Pinot.apply(text, a), Pinot.transform(a, b, Pinot.Left)) ==
    Pinot.apply(Pinot.apply(text, b), Pinot.transform(b, a, Pinot.Right))
```

`priority`は、競合解決においてどの変更が先に行われたかを示すために使用されます。
