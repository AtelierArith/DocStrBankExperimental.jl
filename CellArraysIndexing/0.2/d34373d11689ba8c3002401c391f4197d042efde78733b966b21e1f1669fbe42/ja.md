```
getcellindex(A, cellᵢ, I)
```

特定のセルにおける `cellᵢ` インデックスを取得します `CellArray``。

# 引数

  * `A::CPUCellArray{SVector, nDim, 1, T}`: 検索するCPUCellArray。
  * `cellᵢ::Int`: 取得するセルのインデックス。
  * `I::Vararg{Int, nDim}`: セル内の要素のインデックス。

# 戻り値

  * 指定されたセルのインデックス。
