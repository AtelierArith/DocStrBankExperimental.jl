```julia
cSIL() -> ClusterValidityIndices.cSIL

```

# 概要

重心ベースのシルエット (cSIL) クラスタ有効性インデックスのコンストラクタ。

# 例

```julia
# パッケージをインポート
using ClusterValidityIndices
# cSIL モジュールを構築
my_cvi = cSIL()
```

# 参考文献

1. L. E. Brito da Silva, N. M. Melton, and D. C. Wunsch II, "Incremental Cluster Validity Indices for Hard Partitions: Extensions  and  Comparative Study," ArXiv  e-prints, Feb 2019, arXiv:1902.06711v1 [cs.LG].
2. P. J. Rousseeuw, "Silhouettes: A graphical aid to the interpretation and validation of cluster analysis," Journal of Computational and Applied Mathematics, vol. 20, pp. 53-65, 1987.
3. M. Rawashdeh and A. Ralescu, "Center-wise intra-inter silhouettes," in Scalable Uncertainty Management, E. Hüllermeier, S. Link, T. Fober et al., Eds. Berlin, Heidelberg: Springer, 2012, pp. 406-419.

# メソッドリスト / 定義場所

```julia
cSIL()
```

defined at [`packages/ClusterValidityIndices/UT9rS/src/CVI/cSIL.jl:63`](file:///home/terasaki/.julia/packages/ClusterValidityIndices/UT9rS/src/CVI/cSIL.jl).
