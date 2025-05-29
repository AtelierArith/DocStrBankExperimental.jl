```
extract_close_matches(key, candidates; n=3, cutoff=0.6)
```

指定された `key` に基づいて、`candidates` から最大 `n` の近似一致を見つけて返します。類似度比は、マッチする部分列を比較する `similarity_ratio` 関数を使用して計算されます。

# 引数

  * `key`: 近似一致を求める文字列または列。
  * `candidates`: `key` と比較される文字列または列の配列。

# オプションのキーワード

  * `n`: 返す近似一致の最大数（デフォルトは3）。
  * `cutoff`: 候補が近似一致と見なされるために必要な最小類似度比（デフォルトは0.6）。

# 戻り値

  * `cutoff` を超える類似度比を持つ最大 `n` の候補の配列。

# 例

```julia
julia> mistyped_kw = "iterations";

julia> candidate_kws = ["niterations", "ncycles_per_iteration", "niterations_per_cycle", "abcdef", "iter"];

julia> extract_close_matches(mistyped_kw, candidate_kws)
["niterations", "niterations_per_cycle"]
```
