```
set_labels!(h::HasseDiagram, labs::Dict{Int,T}) where {T}
```

部分順序集合を描画する際に、要素 `j` に `labs[j]` でラベルを付けます。

`labs` が省略された場合、要素 `j` に `j` というデフォルトのラベルにリセットされます。
