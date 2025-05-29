```
invert(text, ops::Vector{Range}) -> Vector{Range}
```

テキストに対する一連の編集が与えられたとき、編集の逆のセットを生成します。

```julia
Pinot.apply(Pinot.apply(text, edits), Pinot.inverse(edits)) == text
```
