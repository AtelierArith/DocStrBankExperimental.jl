```
SubdivisionBasedGrid(grid::NTuple{D, <:AbstractRange}, lvl_array::Array{Int, D})
```

粗い `grid` が状態空間をタイル状に分割している場合、与えられたレベル配列 `lvl_array` に基づいて `SubdivisionBasedGrid` を構築します。このレベル配列は `grid` と同じ次元を持つ必要があります。レベル配列は非負の整数値を持ち、0 は対応する粗い `grid` のセルがこれ以上細分化されないことを意味します。値 `n > 0` は、対応するセルが合計 `2^n` 回細分化されることを意味し（各次元に沿って）、元の粗いセル内により細かいセルが生成されます。
