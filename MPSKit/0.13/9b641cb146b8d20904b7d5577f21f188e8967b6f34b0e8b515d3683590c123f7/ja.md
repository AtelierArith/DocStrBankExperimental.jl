```
approximate(ψ₀, (O, ψ), algorithm, [environments]; kwargs...) -> (ψ, environments)
approximate!(ψ₀, (O, ψ), algorithm, [environments]; kwargs...) -> (ψ, environments)
```

演算子 `O` を状態 `ψ` に適用した近似値を、MPS `ψ₀` の形で計算します。

## 引数

  * `ψ₀::AbstractMPS`: 近似された状態の初期推測
  * `(O::AbstractMPO, ψ::AbstractMPS)`: 近似される演算子 `O` と状態 `ψ`
  * `algorithm`: 近似アルゴリズム。利用可能なアルゴリズムのリストは以下を参照してください。
  * `[environments]`: MPS 環境マネージャー

## キーワード

  * `tol::Float64`: 収束基準の許容誤差
  * `maxiter::Int`: 最大反復回数
  * `verbosity::Int`: 進捗情報の表示

## アルゴリズム

  * `DMRG`: 単一サイトスキームで忠実度を最大化するための交互最小二乗法。
  * `DMRG2`: 二サイトスキームで忠実度を最大化するための交互最小二乗法。
  * `IDMRG`: 熱力学的限界における忠実度密度を最大化するための `DMRG` の変種。
  * `IDMRG2`: 熱力学的限界における忠実度密度を最大化するための `DMRG2` の変種。
  * `VOMPS`: 一様 MPS を切り捨てるための接線空間法。
