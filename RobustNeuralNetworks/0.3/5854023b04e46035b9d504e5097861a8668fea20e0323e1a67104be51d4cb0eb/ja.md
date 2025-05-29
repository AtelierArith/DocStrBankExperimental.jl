```
DirectLBDNParams{T}(nu, nh, ny, γ; <キーワード引数>) where T
```

リプシッツ有界深層ネットワークの直接パラメータ化を構築します。

これは通常、`DirectLBDNParams`の直接パラメータ化を受け取り、それを明示的なパラメータ化に変換するルールを定義する高レベルのコンストラクタによって使用されます。例えば、[`DenseLBDNParams`](@ref)を参照してください。

# 引数

  * `nu::Int`: 入力の数。
  * `nh::Union{Vector{Int}, NTuple{N, Int}}`: 各層の隠れユニットの数。例: `nh = [5,10]` は5ノードと10ノードの2つの隠れ層を示します。
  * `ny::Int`: 出力の数。
  * `γ::Real=T(1)`: リプシッツ上限、正でなければなりません。

# キーワード引数

  * `initW::Function=Flux.glorot_normal`: 暗黙のパラメータ `X,Y,d` の初期化関数。
  * `initb::Function=Flux.glorot_normal`: バイアスベクトルの初期化関数。
  * `learn_γ::Bool=false:` リプシッツ境界 γ を学習可能なパラメータにするかどうか。
  * `rng::AbstractRNG = Random.GLOBAL_RNG`: モデル初期化のためのrng。

パラメータ化の詳細については、[Wang et al. (2023)](https://proceedings.mlr.press/v202/wang23v.html)を参照してください。

また、[`DenseLBDNParams`](@ref)も参照してください。
