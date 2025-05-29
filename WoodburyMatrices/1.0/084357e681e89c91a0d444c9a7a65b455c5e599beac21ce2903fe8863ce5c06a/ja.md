```
W = SymWoodbury(A, B, D; allocatetmp::Bool=false)
```

行列 `W = A + BDBᵀ` の形を表します。ここで、`A` と `D` は対称です。方程式 `Wx = b` は [ウッドベリー行列の恒等式](https://en.wikipedia.org/wiki/Woodbury_matrix_identity) を使用して解かれます。

方程式を解くことが主な目的である場合、`A` を因子分解として提供することが有利です（例えば、`A` が正定値半定行列である場合は `SymWoodbury(cholesky(A), B, D)`）。

これにより、`A` が対称であることが確認されます。`Symmetric` 行列または因子分解を渡すことでチェックを省略できます。

また、`allocatetmp` が説明されている [Woodbury](@ref) も参照してください。
