```
fitprior2(data, algo, diss = false;
Kmin = 1,
Kmax = Int(floor(size(data)[end] / 2),
verbose = true)
```

データから最適な事前ハイパーパラメータを決定します。$\sigma$、$\eta$、$u$、および$v$の値を取得するために[`fitprior`](@ref)と同じ方法を使用しますが、$K$クラスタのすべての値に対してクラスタリングの内部クラスタおよびクロスクラスタ距離を考慮することによってクラスタ特有のパラメータの値を導出します。$K \in [K_\mathrm{min}, K_\mathrm{max}]$の範囲内での$K$の事前予測分布によって重み付けされます。

# 必要な引数

  * `data::Union{Vector{Vector{Float64}}, Matrix{Float64}}`: (多次元)観測のベクトル、または各列が観測である行列、またはペアワイズの非類似性の平方行列のいずれかである必要があります。
  * `algo::String`: `"k-means"`または`"k-medoids"`のいずれかでなければなりません。

# オプションの引数

  * `diss::bool`: trueの場合、`data`はペアワイズの非類似性行列であると見なされます。
  * `Kmin::Integer`: エルボー法のためにスキャンするクラスタの最小数。
  * `Kmax::Integer`: エルボー法のためにスキャンするクラスタの最大数。指定しない場合、観測数の半分に設定されます。
  * `verbose::Bool`: falseの場合、すべての情報メッセージと進行状況バーが無効になります。

# 戻り値

[`PriorHyperparamsList`](@ref)型のオブジェクト。
