```
NUTS(n_adapts::Int, δ::Float64; max_depth::Int=10, Δ_max::Float64=1000.0, init_ϵ::Float64=0.0; adtype::ADTypes.AbstractADType=AutoForwardDiff()
```

ノー・ユー・ターン・サンプラー (NUTS) サンプラー。

使用法：

```julia
NUTS()            # デフォルトのNUTS設定を使用します。
NUTS(1000, 0.65)  # 1000の適応ステップと、目標受け入れ率0.65を使用します。
```

引数：

  * `n_adapts::Int` : 適応に使用するサンプルの数。
  * `δ::Float64` : 二重平均のための目標受け入れ率。
  * `max_depth::Int` : 最大の二重木の深さ。
  * `Δ_max::Float64` : 二重木の間の最大発散。
  * `init_ϵ::Float64` : 初期ステップサイズ；0はヒューリスティック手法を使用して自動的に探索することを意味します。
  * `adtype::ADTypes.AbstractADType` : 自動微分 (AD) バックエンド。指定されていない場合、`ForwardDiff` が使用され、その `chunksize` は自動的に決定されます。
