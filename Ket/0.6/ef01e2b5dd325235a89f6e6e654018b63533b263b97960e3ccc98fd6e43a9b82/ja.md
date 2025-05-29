```
 applymap!(result::Matrix, Φ::AbstractMatrix, M::AbstractMatrix)
```

Choi-Jamiołkowski 演算子 `Φ` によって与えられた CP マップを、行列 `M` に対して割り当てやラッピングを行わずに適用します。対称またはエルミートの場合は、上三角のみが計算されます。`result` はサイズ `dout × dout` の行列でなければならず、`size(M, 1) * dout == size(Φ, 1)` である必要があります。
