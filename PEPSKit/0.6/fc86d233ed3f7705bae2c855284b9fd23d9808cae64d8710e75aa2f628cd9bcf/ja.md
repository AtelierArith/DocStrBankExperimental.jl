```julia
struct GeomSum{F} <: PEPSKit.GradMode{F}
```

幾何和の明示的評価を使用したCTMRGの勾配モード。

## フィールド

  * `tol::Real`
  * `maxiter::Int64`
  * `verbosity::Int64`

## コンストラクタ

```
GeomSum(; kwargs...)
```

以下のキーワード引数に基づいて`GeomSum`アルゴリズム構造体を構築します：

  * `tol::Real=1.0e-6` : 幾何和における2つの連続する和項のノルムの差の収束許容誤差。
  * `maxiter::Int=30` : 勾配反復の最大数。
  * `verbosity::Int=-1` : 出力情報の冗長性で、以下のいずれかになります：

    0. 出力情報を抑制
    1. 収束警告を表示
    2. 各勾配反復での情報
  * `iterscheme::Symbol=:fixed` : 微分されるCTMRG反復のスタイルで、以下のいずれかになります：

      * `:fixed` : 微分されたCTMRG反復は、固定されたゲージのセットを使用した事前計算されたSVDを使用します
      * `:diffgauge` : 微分された反復はCTMRG反復とその後のゲージ固定ステップで構成され、ゲージ固定手順も微分されます
