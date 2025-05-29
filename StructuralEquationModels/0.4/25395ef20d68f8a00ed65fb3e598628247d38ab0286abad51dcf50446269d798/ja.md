リッジ正則化。

# コンストラクタ

```
SemRidge(;α_ridge, which_ridge, nparams, parameter_type = Float64, implied = nothing, kwargs...)
```

# 引数

  * `α_ridge`: ペナルティ項のハイパーパラメータ
  * `which_ridge::Vector`: 正則化すべきパラメータを示すパラメータラベル（シンボル）またはインデックスのベクター。
  * `nparams::Int`: モデルのパラメータの数
  * `implied::SemImplied`: モデルの暗示部分
  * `parameter_type`: パラメータの型

# 例

```julia
my_ridge = SemRidge(;α_ridge = 0.02, which_ridge = [:λ₁, :λ₂, :ω₂₃], nparams = 30, implied = my_implied)
```

# インターフェース

解析的な勾配とヘッセ行列が利用可能です。
