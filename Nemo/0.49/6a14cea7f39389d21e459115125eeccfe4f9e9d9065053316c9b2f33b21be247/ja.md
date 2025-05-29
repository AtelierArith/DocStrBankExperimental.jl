```
eigenspaces(M::MatElem{T}; side::Symbol = :left)
  where T <: FieldElem -> Dict{T, MatElem{T}}
```

$$
M
$$

の固有値をキーとし、対応する固有空間の基底を値とする辞書を返します。sideが`:right`の場合は右固有空間が計算され、`:left`の場合は左固有空間が計算されます。

`eigenspace`も参照してください。
