```julia
struct EigSolver{F} <: PEPSKit.GradMode{F}
```

勾配線形問題を固有値問題として解くための `KrylovKit.KrylovAlgorithm` の勾配モードラッパーです。

## フィールド

  * `solver_alg::KrylovKit.KrylovAlgorithm`

## コンストラクタ

```
EigSolver(; kwargs...)
```

以下のキーワード引数に基づいて `EigSolver` アルゴリズム構造体を構築します：

  * `tol::Real=1.0e-6` : 固有値ソルバーの収束許容誤差。
  * `maxiter::Int=30` : ソルバーの最大反復回数。
  * `verbosity::Int=-1` : 線形ソルバーの出力情報の冗長性。
  * `iterscheme::Symbol=:fixed` : 微分されるCTMRG反復のスタイルで、次のいずれかになります：

      * `:fixed` : 微分されたCTMRG反復は、固定されたゲージのセットを用いた事前計算されたSVDを使用します
      * `:diffgauge` : 微分された反復はCTMRG反復とその後のゲージ固定ステップから成り、ゲージ固定手続きも微分されます
  * `solver_alg::Union{KrylovKit.KrylovAlgorithm,NamedTuple}=(; alg=:arnoldi` : 固有値ソルバーアルゴリズムで、直接 `KrylovKit.KrylovAlgorithm` として供給される場合、上記で指定された `tol`、`maxiter` および `verbosity` を上書きします。あるいは、`NamedTuple` を介して供給されることもでき、その場合 `alg` は次のいずれかになります：

      * `:arnoldi` : アーノルディKrylovアルゴリズム、詳細については [`KrylovKit.Arnoldi`](@extref) を参照してください

```
