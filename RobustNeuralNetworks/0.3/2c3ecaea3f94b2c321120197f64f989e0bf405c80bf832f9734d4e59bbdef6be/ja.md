```
DenseLBDNParams{T}(nu, nh, ny, γ; <keyword arguments>) where T
```

密な（全結合）LBDNの直接パラメータ化を構築します。

これは、保証されたリプシッツ境界 `γ` を持つ多層パーセプトロン（例: `Flux.Dense`）に相当します。リプシッツ境界は学習可能なパラメータにすることができます。

# 引数

  * `nu::Int`: 入力の数。
  * `nh::Union{Vector{Int}, NTuple{N, Int}}`: 各層の隠れユニットの数。例: `nh = [5,10]` は5および10ノードの2つの隠れ層を示します。
  * `ny::Int`: 出力の数。
  * `γ::Real=T(1)`: リプシッツ上限、正でなければなりません。

# キーワード引数:

  * `nl::Function=relu`: セクター制限された静的非線形性。
  * `learn_γ::Bool=false:` リプシッツ境界 γ を学習可能なパラメータにするかどうか。

キーワード引数 `initW`、`initb`、`rng` のドキュメントについては [`DirectLBDNParams`](@ref) を参照してください。
