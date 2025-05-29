```julia
struct LinSolver{F} <: PEPSKit.GradMode{F}
```

勾配線形問題を反復ソルバーを使用して解くための `KrylovKit.LinearSolver` の勾配モードラッパーです。

## フィールド

  * `solver_alg::KrylovKit.LinearSolver`

## コンストラクタ

```
LinSolver(; kwargs...)
```

以下のキーワード引数に基づいて `LinSolver` アルゴリズム構造体を構築します：

  * `tol::Real=1.0e-6` : 線形ソルバーの収束許容誤差。
  * `maxiter::Int=30` : ソルバーの最大反復回数。
  * `verbosity::Int=-1` : 線形ソルバーの出力情報の冗長性。
  * `iterscheme::Symbol=:fixed` : 微分されるCTMRG反復のスタイルで、次のいずれかになります：

      * `:fixed` : 微分されたCTMRG反復は、固定されたゲージのセットを使用して事前に計算されたSVDを使用します
      * `:diffgauge` : 微分された反復はCTMRG反復とその後のゲージ固定ステップで構成され、ゲージ固定手順も微分されます
  * `solver_alg::Union{KrylovKit.LinearSolver,NamedTuple}=(; alg::Symbol=:bicgstab` : 線形ソルバーアルゴリズムで、直接 `KrylovKit.LinearSolver` として供給される場合、上記で指定された `tol`、`maxiter` および `verbosity` を上書きします。あるいは、`NamedTuple` を介して供給されることもでき、`alg` は次のいずれかになります：

      * `:gmres` : GMRES反復線形ソルバー、詳細は [`KrylovKit.GMRES`](@extref) を参照してください
      * `:bicgstab` : BiCGStab反復線形ソルバー、詳細は [`KrylovKit.BiCGStab`](@extref) を参照してください
