```
guesswork(
    p::AbstractVector{T},
    ρBs::AbstractVector{<:AbstractMatrix};
    solver,
    K::Integer = length(p),
    c = T[1:K..., 5_000],
    dual::Bool = false,
    remove_repetition::Bool = true,
    povm_outcomes = make_povm_outcomes(length(p), K, remove_repetition),
    verbose::Bool = true,
)
```

確率ベクトル `p` によって指定された c-q 状態のための推測作業を計算し、分布 `X` と関連する量子状態 `ρBs` を与えます。

キーワード引数は次のとおりです：

  * `solver` は唯一の必須キーワード引数です。SCS や MOSEK などの SDP ソルバーを渡す必要があります。
  * `K` は許可される最大推測数に対応します。プライマル SDP の変数の数（およびデュアル SDP の制約の数）は `length(p)^K` にスケールします。
  * `c` はカスタムコストベクトルを指定できます。`K < length(p)` の場合、`c` は長さ `K+1` である必要があります。最後のエントリ `c[K+1]` は、`K` 回の推測内で正しい答えを推測しなかった場合のコストに対応します。
  * `dual` は、プライマルまたはデュアル最適化問題を解くべきかどうかを示すブール変数です。
  * `remove_repetition` はデフォルトで true のブール変数で、同じ値の繰り返し推測を削除するかどうかを示します。`c` が増加している限り、これは最適値に影響を与えずに SDP のサイズを減少させます。
  * `povm_outcomes` は、可能な推測順序に対応するイテレータ（またはベクトル）である必要があります。これは、重複なしで `1:length(p)` の長さ `K` のすべての部分集合にデフォルト設定されます。
  * `verbose` は、問題が最適に解決されない場合に警告を印刷するかどうかを示すブール値です。
