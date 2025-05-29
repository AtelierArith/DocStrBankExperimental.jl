```
DirectRENParams{T}(nu, nx, nv; <キーワード引数>) where T
```

（非循環的な）再帰的平衡ネットワークの直接パラメータ化を構築します。

これは通常、RENを定義する際に高レベルのコンストラクタによって使用され、直接パラメータ化を取り込み、それを明示的なパラメータ化に変換するためのルールを定義します。例えば、[`GeneralRENParams`](@ref)を参照してください。

# 引数

  * `nu::Int`: 入力の数。
  * `nx::Int`: 状態の数。
  * `nv::Int`: ニューロンの数。

# キーワード引数

  * `init=:randomQR`: 初期化方法。オプションは次の通りです：

      * `:random`: Glorot正規分布によるランダムサンプリング。通常、「速い」/短期記憶動的モデルをサンプリングします。
      * `:randomQR:` `glorot_normal`で`X`を計算し、QR分解`X = qr(X).Q`を取ります。長期記憶が必要な場合に、`X`を単位行列に近づけて初期化するのに適しています。デフォルトはレガシーとして。
      * `:cholesky`: `H`のコレスキー分解を用いて`X`を計算し、`E,F,P = I`を設定します。遅い/長期記憶動的モデルに適しています。
  * `polar_param::Bool=true`: RENパラメータ化において`X`から`H`行列を構築するために極座標パラメータ化を使用します（推奨）。
  * `D22_free::Bool=false`: `D22`を自由パラメータとして訓練するか（`true`）、`X3, Y3, Z3`から別に構築するか（`false`）を指定します。通常、収縮RENの場合のみ`D22_free = true`を使用します。
  * `D22_zero::Bool=false`: フィードスルーを除去するために`D22 = 0`に固定します。
  * `bx_scale::T=0`: 初期状態バイアスベクトル`bx`のスケールを設定します。
  * `bv_scale::T=1`: 初期ニューロン入力バイアスベクトル`bv`のスケールを設定します。
  * `output_map::Bool=true`: 出力層を含めます $y_t = C_2 x_t + D_{21} w_t + D_{22} u_t + b_y$。そうでない場合、出力は単に $y_t = x_t$ です。
  * `ϵ::T=1e-12`: 正定値行列のための正則化パラメータ。
  * `rng::AbstractRNG=Random.GLOBAL_RNG`: モデル初期化のためのrng。

パラメータ化の詳細については、[Revay et al. (2021)](https://arxiv.org/abs/2104.05942)を参照してください。

また、[`GeneralRENParams`](@ref)、[`ContractingRENParams`](@ref)、[`LipschitzRENParams`](@ref)、[`PassiveRENParams`](@ref)も参照してください。
