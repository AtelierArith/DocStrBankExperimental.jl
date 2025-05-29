greedy*interpolation(s::LandmarkSelectionStrategy, κ, X, l, f*X::T = nothing) greedy_interpolation(s, κ, X, l, f::Function)

関数 `f` のカーネル補間を、戦略 `s` に従って `X` から貪欲に選ばれた `l` のランドマークを使用して構築します。戻り値はタプル `(Z, w)` で、`Z` はランドマーク (d×l) であり、`w` は重みのベクトル (長さ l) または `compute_weights` の値に応じて `nothing` です。

引数:

  * s: ランドマークを選択するための戦略。
  * κ: カーネル関数。
  * X: データ (列 = サンプル)。
  * l: 補間点の数。
  * f*X: 評価のベクトル [f(x₁),…,f(x*n)]ᵀ。

キーワード引数:

  * `compute_weights` (=`false`): 基底 ϕ(z*1),…,ϕ(z*m) における f の重みを計算するかどうかを示すブール値。

警告: 重みは反復的に計算されますが、数値的に安定していない方法で行われます。最初の反復ではうまく機能する可能性がありますが、`l` の値が大きくなるとパフォーマンスが低下する可能性があります。このため、`compute_weights` のデフォルトは `false` です。
