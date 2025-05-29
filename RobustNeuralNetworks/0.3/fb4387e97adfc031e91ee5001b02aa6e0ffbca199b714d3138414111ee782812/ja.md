```
GeneralRENParams{T}(nu, nx, nv, ny, Q, S, R; <keyword arguments>) where T
```

一般的な行動制約を満たすRENの直接パラメータ化を構築します。

行動制約は、増分積分二次制約（IQC）における行列`Q,S,R`によって符号化されます。詳細は[Revay et al. (2021)](https://arxiv.org/abs/2104.05942)の式4を参照してください。

# 引数

  * `nu::Int`: 入力の数。
  * `nx::Int`: 状態の数。
  * `nv::Int`: ニューロンの数。
  * `ny::Int`: 出力の数。
  * `Q::AbstractMatrix`: モデル出力に対するIQC重み行列
  * `S::AbstractMatrix`: モデル出力/入力に対するIQC結合行列
  * `R::AbstractMatrix`: モデル出力に対するIQC重み行列

# キーワード引数

  * `nl::Function=relu`: セクタ制約付き静的非線形性。
  * `αbar::T=1`: 縮小率の上限で、`ᾱ ∈ (0,1]`。

キーワード引数`init`、`ϵ`、`bx_scale`、`bv_scale`、`polar_param`、`rng`のドキュメントについては[`DirectRENParams`](@ref)を参照してください。

また、[`ContractingRENParams`](@ref)、[`LipschitzRENParams`](@ref)、[`PassiveRENParams`](@ref)も参照してください。
