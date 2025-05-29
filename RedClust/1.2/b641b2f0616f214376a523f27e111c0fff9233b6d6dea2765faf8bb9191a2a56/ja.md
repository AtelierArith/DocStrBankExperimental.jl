```
fitprior(data, algo, diss = false;
Kmin = 1,
Kmax = Int(floor(size(data)[end] / 2),
verbose = true)
```

データから最適な事前ハイパーパラメータを決定します。k-meansまたはk-medoidsとエルボー法を使用して概念的クラスタリングを取得し、距離を概念的クラスタリングに基づいてクラスタ内距離とクラスタ間距離に分割します。これらの距離は、MLEおよび経験的ベイズサンプリングを使用して事前ハイパーパラメータをフィットさせるために使用されます。

# 必要な引数

  * `data::Union{Vector{Vector{Float64}}, Matrix{Float64}}`: 可能性のある多次元観測のベクトル、または各列が観測値である行列、またはペアワイズの非類似性の平方行列である必要があります。
  * `algo::String`: `"k-means"`または`"k-medoids"`のいずれかである必要があります。

# オプションの引数

  * `diss::bool`: trueの場合、`data`はペアワイズの非類似性行列であると見なされます。
  * `Kmin::Integer`: エルボー法でスキャンするクラスタの最小数。
  * `Kmax::Integer`: エルボー法でスキャンするクラスタの最大数。指定しない場合は、観測値の数の半分に設定されます。
  * `verbose::Bool`: falseの場合、すべての情報メッセージと進行状況バーが無効になります。

# 戻り値

[`PriorHyperparamsList`](@ref)型のオブジェクト。
