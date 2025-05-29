```
ContractingRENParams{T}(nu, nx, nv, ny; <keyword arguments>) where T
```

収縮RENの直接パラメータ化を構築します。

これらのパラメータは、保証された組み込みの収縮特性を持つ明示的な [`REN`](@ref) モデルを構築するために使用できます。

# 引数

  * `nu::Int`: 入力の数。
  * `nx::Int`: 状態の数。
  * `nv::Int`: ニューロンの数。
  * `ny::Int`: 出力の数。

# キーワード引数

  * `nl::Function=relu`: セクター制約のある静的非線形性。
  * `αbar::T=1`: 収縮率の上限で、`ᾱ ∈ (0,1]`。

キーワード引数 `init`、`ϵ`、`bx_scale`、`bv_scale`、`polar_param`、`D22_zero`、`output_map`、`rng` のドキュメントについては、[`DirectRENParams`](@ref) を参照してください。

また、[`GeneralRENParams`](@ref)、[`LipschitzRENParams`](@ref)、[`PassiveRENParams`](@ref) も参照してください。
