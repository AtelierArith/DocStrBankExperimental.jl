```
QDHT{p, n}(R, N; dim=1)
QDHT([p, ] R, N; dim=1)
QDHT(p, [n, ] R, N; dim=1)
```

`p`-次の準離散ハンケル変換は、半径 `R` の開口部で `N` サンプルを持ち、次元 `dim` に沿って変換します。指定がない場合、`p` は 0 にデフォルト設定され、球面次元 `n` は 1（円筒）にデフォルト設定されます。

その後：

[1] L. Yu, M. Huang, M. Chen, W. Chen, W. Huang, and Z. Zhu, Optics Letters 23 (1998)

[2] M. Guizar-Sicairos and J. C. Gutiérrez-Vega, JOSA A 21, 53 (2004)

[3] H. F. Johnson, Comput. Phys. Commun., 43, 2 (1987)

ただし、いくつかの変更があります：

変換行列 T は [1, 2] で定義された C/T と同じではなく、[3] の式 14 で使用される形式に近いです。$J_1(α_{pn}) J_1(α_{pm})$ で割る代わりに、$J_1(α_{pn})^2$ で割ります。これにより、$f$ と $F$ の間の因子がキャンセルされるため、変換行列を適用する前後で $J_1(α_{pn})$ ($J_1(α_{pm})$) で掛け算（割り算）する必要がなくなります。

[`AbstractFFT`](https://github.com/JuliaMath/AbstractFFTs.jl) のアプローチに従い、`mul` と `ldiv` を使用して前方および逆変換を適用します。

`QDHT` を使用してサンプリングされた関数の放射状積分を計算するには、[`integrateR`](@ref) と [`integrateK`](@ref) を使用します。

係数の型は `R` の型から推測されます（ただし、少なくとも `Float` に昇格されます）。したがって、任意の精度を使用するには `QDHT([p, ] BigFloat(R), ...)` を使用します。
