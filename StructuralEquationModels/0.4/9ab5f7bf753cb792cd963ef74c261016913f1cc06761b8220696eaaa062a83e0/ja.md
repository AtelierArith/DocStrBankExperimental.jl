最大尤度推定。

# コンストラクタ

```
SemML(;observed, meanstructure = false, approximate_hessian = false, kwargs...)
```

# 引数

  * `observed::SemObserved`: モデルの観測部分
  * `meanstructure::Bool`: モデルに平均構造はありますか？
  * `approximate_hessian::Bool`: ヘッセ行列に基づく最適化が使用される場合、ヘッセ行列を近似に置き換えるべきですか？

# 例

```julia
my_ml = SemML(observed = my_observed)
```

# インターフェース

解析的勾配が利用可能であり、平均構造がないモデルおよびRAMSymbolic暗示型の場合、解析的ヘッセ行列も利用可能です。
