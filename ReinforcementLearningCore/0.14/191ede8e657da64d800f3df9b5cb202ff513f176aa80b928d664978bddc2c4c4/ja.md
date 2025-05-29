```
generalized_advantage_estimation(rewards::VectorOrMatrix, values::VectorOrMatrix, γ::Number, λ::Number;kwargs...)
```

現在のステップから始まる一般化されたアドバンテージ推定を計算します。割引率は `γ` で、GAE-Lambda のためのラムダは 'λ' です。`rewards` と 'values' は行列である可能性があります。

# キーワード引数

  * `dims=:`, `rewards` が `Matrix` の場合、`dims` は `1` または `2` のみです。
  * `terminal=nothing`, 各報酬が端末に続くかどうかを指定します。`nothing` はゲームがまだ終了していないことを意味します。`terminal` が提供される場合、そのサイズは `rewards` と同じでなければなりません。

# 例

```
