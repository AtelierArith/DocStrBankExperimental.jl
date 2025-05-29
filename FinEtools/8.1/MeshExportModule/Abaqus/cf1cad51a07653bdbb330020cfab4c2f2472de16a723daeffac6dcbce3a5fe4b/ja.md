```
*ELEMENT(self::AbaqusExporter, TYPE::AbstractString, ELSET::AbstractString,
  start::Integer, conn::AbstractArray{T, 2}) where {T<:Integer}
```

`*ELEMENT`オプションを記述します。

`TYPE`= 要素タイプコード、`ELSET`= 要素が属する要素セット、`start`= この整数から要素番号を開始、`conn`= 要素の接続配列、要素ごとに1行
