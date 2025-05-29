```
LipschitzRENParams(nu, nx, nv, ny, γ; <keyword arguments>) where T
```

Lipschitz境界がγのRENの直接パラメータ化を構築します。

# 引数

  * `nu::Int`: 入力の数。
  * `nx::Int`: 状態の数。
  * `nv::Int`: ニューロンの数。
  * `ny::Int`: 出力の数。
  * `γ::Number`: Lipschitz上限。

# キーワード引数

  * `nl::Function=relu`: セクター制限された静的非線形性。
  * `αbar::T=1`: 縮小率の上限で、`ᾱ ∈ (0,1]`。
  * `learn_γ::Bool=false:` Lipschitz境界γを学習可能なパラメータにするかどうか。

キーワード引数`init`、`ϵ`、`bx_scale`、`bv_scale`、`polar_param`、`D22_zero`、`rng`のドキュメントについては[`DirectRENParams`](@ref)を参照してください。

また、[`GeneralRENParams`](@ref)、[`ContractingRENParams`](@ref)、[`PassiveRENParams`](@ref)も参照してください。
