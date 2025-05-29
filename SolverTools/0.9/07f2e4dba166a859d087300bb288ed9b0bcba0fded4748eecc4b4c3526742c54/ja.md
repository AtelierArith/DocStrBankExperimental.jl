ARTrustRegion(α₀::T;kwargs...)

`TRARC`アルゴリズムで使用される主なパラメータを選択します。`α₀`は初期TR/ARCパラメータです。キーワード引数は次のとおりです。

  * `max_α::T`: `α`の最大値。デフォルトは`T(1) / sqrt(eps(T))`。
  * `acceptance_threshold::T`: ステップが成功するための比率。デフォルトは`T(0.1)`。
  * `increase_threshold::T`: `α`を増加させるための比率。デフォルトは`T(0.75)`。
  * `reduce_threshold::T`: `α`を減少させるための比率。デフォルトは`T(0.1)`。
  * `increase_factor::T`: `α`の増加ファクター。デフォルトは`T(5.0)`。
  * `decrease_factor::T`: `α`の減少ファクター。デフォルトは`T(0.1)`。
  * `max_unsuccinarow::Int`: 連続した不成功な反復の数の制限。デフォルトは`30`。

`ARTrustRegion`構造体を返します。

これは`TrustRegion`または`TRONTrustRegion`と比較できます。
