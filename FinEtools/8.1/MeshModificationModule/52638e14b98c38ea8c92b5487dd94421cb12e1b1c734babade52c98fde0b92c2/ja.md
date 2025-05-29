```
interior2boundary(interiorconn::Array{IT,2}, extractb::Array{IT,2}) where {IT<:Integer}
```

内部の接続から境界の接続を抽出します。

`extractb` = 境界面がどの順序で移動されるかを定義する配列。例えば、四面体の場合、この配列は `extractb = [1 3 2; 1 2 4; 2 3 4; 1 4 3]` です。
