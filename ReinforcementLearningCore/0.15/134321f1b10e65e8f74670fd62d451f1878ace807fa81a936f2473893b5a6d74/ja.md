```
discount_rewards(rewards::VectorOrMatrix, γ::Number;kwargs...)
```

現在のステップから始まる利得を割引率 `γ` で計算します。`rewards` は行列であることができます。

# キーワード引数

  * `dims=:`, `rewards` が `Matrix` の場合、`dims` は `1` または `2` のみです。
  * `terminal=nothing`, 各報酬が端末に続くかどうかを指定します。`nothing` はゲームがまだ終了していないことを意味します。`terminal` が提供される場合、サイズは `rewards` と同じでなければなりません。
  * `init=nothing`, `init` は最後の状態の報酬推定を提供するために使用できます。

# 例
