```
W = Woodbury(A, U, C, V; allocatetmp::Bool=false)
```

行列 `W = A + UCV` を表します。方程式 `Wx = b` は [Woodbury行列の恒等式](https://en.wikipedia.org/wiki/Woodbury_matrix_identity) を使用して解かれます。

方程式を解くことが主な目的である場合、`A` を因数分解として提供することがしばしば有利です（例： `Woodbury(lu(A), U, C, V)`）。

`allocatetmp` が true の場合、乗算および除算の中間ステップで使用される一時ストレージが割り当てられます。

!!! warning
    同じ `W` を複数のスレッドで使用する場合は、`allocatetmp=false` を使用するか、データ競合のリスクがあります。


関連情報として [SymWoodbury](@ref) を参照してください。
