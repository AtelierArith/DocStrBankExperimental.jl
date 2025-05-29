```
Problem{T}
```

軌道最適化問題。軌道最適化問題の完全な定義を含みます：

  * 動力学モデル（`RD.DiscreteDynamics`）
  * 目的（[`Objective`](@ref)）
  * 制約（[`ConstraintList`](@ref)）
  * 初期状態と最終状態
  * プライマル変数（状態と制御軌道）
  * 離散化情報：ノットポイント（`N`）、時間ステップ（`dt`）、および総時間（`tf`）

# コンストラクタ：

```julia
Problem(model, obj, constraints, x0, xf, Z, N, tf)
Problem(model, obj, x0, tf; [xf, constraints, N, X0, U0, dt, integration])
```

ここで、`Z`は[`RobotDynamics.SampledTrajectory`]です。

# 引数

  * `model`: `DiscreteDynamics`モデル。`ContinuousDynamics`モデルが提供された場合、`integration`キーワード引数で指定された積分器を介して`DiscretizedDynamics`モデルに変換されます。
  * `obj`: 目的
  * `X0`: 初期状態軌道。省略するとNaNで初期化され、後でソルバーによって上書きされます。
  * `U0`: 初期制御軌道。省略するとゼロで初期化されます。
  * `x0`: 初期状態
  * `xf`: 最終状態。デフォルトはゼロです。
  * `dt`: 時間ステップ。長さ`N-1`のベクトルまたは正の実数である必要があります。
  * `tf`: 最終時間。ゼロに設定されます。
  * `N`: ノットポイントの数。目的の長さを使用します。
  * `integration`: 連続動力学モデルを離散化するために定義された積分タイプの1つ。

`X0`と`U0`は、`Matrix`または`Vector{<:AbstractVector}`のいずれかであることができます。
