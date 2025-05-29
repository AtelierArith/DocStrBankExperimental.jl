```julia
DB() -> ClusterValidityIndices.DB

```

# 概要

Davies-Bouldin (DB) クラスタ妥当性指標のコンストラクタ。

# 例

```julia
# パッケージをインポート
using ClusterValidityIndices
# DB モジュールを構築
my_cvi = DB()
```

# 参考文献

1. D. L. Davies と D. W. Bouldin, "A cluster separation measure," IEEE Transaction on Pattern Analysis and Machine Intelligence, vol. 1, no. 2, pp. 224-227, Feb. 1979.
2. M. Moshtaghi, J. C. Bezdek, S. M. Erfani, C. Leckie, と J. Bailey, "Online Cluster Validity Indices for Streaming Data," ArXiv e-prints, 2018, arXiv:1801.02937v1 [stat.ML]. [オンライン].
3. M. Moshtaghi, J. C. Bezdek, S. M. Erfani, C. Leckie, J. Bailey, "Online cluster validity indices for performance monitoring of streaming data clustering," Int. J. Intell. Syst., pp. 1-23, 2018.

# メソッドリスト / 定義場所

```julia
DB()
```

[`packages/ClusterValidityIndices/UT9rS/src/CVI/DB.jl:63`](file:///home/terasaki/.julia/packages/ClusterValidityIndices/UT9rS/src/CVI/DB.jl) で定義されています。
