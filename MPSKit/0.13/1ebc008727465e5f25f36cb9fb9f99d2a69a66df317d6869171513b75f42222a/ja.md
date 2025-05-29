```
leading_boundary(ψ₀, O, [environments]; kwargs...) -> (ψ, environments, ϵ)
leading_boundary(ψ₀, O, algorithm, environments) -> (ψ, environments, ϵ)
```

演算子 `O` のためのリーディングバウンダリー MPS を初期推測 `ψ` で計算します。指定されていない場合、提供されたキーワードに基づいて最適化アルゴリズムが試みられます。

## 引数

  * `ψ₀::AbstractMPS`: 初期推測
  * `O::AbstractMPO`: リーディングバウンダリーを見つけるための演算子
  * `[environments]`: MPS 環境マネージャ
  * `algorithm`: 最適化アルゴリズム

## キーワード

  * `tol::Float64`: 収束基準の許容誤差
  * `maxiter::Int`: 最大反復回数
  * `verbosity::Int`: 進行状況情報の表示

## 戻り値

  * `ψ::AbstractMPS`: 収束したリーディングバウンダリー MPS
  * `environments`: 収束した境界に対応する環境
  * `ϵ::Float64`: アルゴリズム終了時の最終収束誤差
