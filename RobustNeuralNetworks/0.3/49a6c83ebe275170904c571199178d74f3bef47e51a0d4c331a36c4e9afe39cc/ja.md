```
PassiveRENParams{T}(nu, nx, nv, ny, ν, ρ; <keyword arguments>) where T
```

受動RENの直接パラメータ化を構築します。

# 引数

  * `nu::Int`: 入力の数。
  * `nx::Int`: 状態の数。
  * `nv::Int`: ニューロンの数。
  * `ny::Int`: 出力の数。
  * `ν::Number=0`: 受動性指数。増分的に厳密に入力受動モデルには `ν > 0` を使用します。増分的受動モデルには `ν = 0` と `ρ = 0` の両方を設定します。
  * `ρ::Number=0`: 受動性指数。増分的に厳密に出力受動モデルには `ρ > 0` を使用します。

受動RENのためには、受動性指数の積 ρν が 1/4 未満である必要があります。

# キーワード引数

  * `nl::Function=relu`: セクター制限された静的非線形性。
  * `αbar::T=1`: 縮小率の上限で、`ᾱ ∈ (0,1]`。

キーワード引数 `init`、`ϵ`、`bx_scale`、`bv_scale`、`polar_param`、`rng` のドキュメントについては [`DirectRENParams`](@ref) を参照してください。

また、[`GeneralRENParams`](@ref)、[`ContractingRENParams`](@ref)、[`LipschitzRENParams`](@ref) も参照してください。
