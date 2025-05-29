```
lanczos(N::Int,nodes::AbstractVector{<:Real},weights::AbstractVector{<:Real};removezeroweights::Bool=true)
```

ランツォス手法–-ノードと重みが与えられたとき、この関数は対応する離散直交多項式の最初の `N` 再帰係数を生成します。

ゼロ重みを削除する必要がある場合は、ブール値 `removezeroweights` を `true` に設定してください。

このスクリプトは、W.B. Gragg と W.J. Harrod の論文 *The numerically stable reconstruction of Jacobi matrices from spectral data*, Numer. Math. 44 (1984), 317-335 のルーチン RKPW から適応されています。
