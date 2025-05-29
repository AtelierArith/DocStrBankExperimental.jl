```
Figure(workstation::Tuple{Float64, Float64}, plots::Vector{PlotObject})
```

新しい図を返します。定義は以下の通りです：

  * **`workstation`**: 幅と高さを持つ `Tuple{Float64, Float64}` で、全体のプロットコンテナ（ワークステーション）のピクセル単位のサイズです。
  * **`plots`**: 図に含まれる個々のプロットの情報を含む [`PlotObject`](@ref) 要素のベクターです。
