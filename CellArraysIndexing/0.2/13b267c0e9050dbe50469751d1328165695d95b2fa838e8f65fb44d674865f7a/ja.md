```
setcellindex!(A, v, cellᵢ, I)
```

特定のセルの`cellᵢ`インデックスをスカラー`v`の値に設定します`CellArray``。

# 引数

  * `A::CPUCellArray{SVector, nDim, 1, T}`: 検索するCPUCellArray。
  * `v<:Real`: セルインデックスの新しい値。
  * `cellᵢ::Int`: 取得するセルのインデックス。
  * `I::Vararg{Int, nDim}`: セル内の要素のインデックス。

# 戻り値

  * 指定されたセルのインデックス。
