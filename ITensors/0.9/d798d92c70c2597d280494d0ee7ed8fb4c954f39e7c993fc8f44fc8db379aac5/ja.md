```
delta([::Type{ElT} = Float64, ]inds)
delta([::Type{ElT} = Float64, ]inds::Index...)
```

すべての対角要素が `one(ElT)` の均一な対角ITensorを作成します。対角要素は1つだけ保存されます。

この関数にはエイリアス `δ` があります。
