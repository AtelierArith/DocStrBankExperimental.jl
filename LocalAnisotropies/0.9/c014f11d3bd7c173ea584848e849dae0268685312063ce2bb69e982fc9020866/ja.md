```
LocalInterpolate(params ...)
```

例: MW = LocalKriging(:MovingWindows, lpars, γ) data |> Select(:var) |> LocalInterpolate(domain, model=MW, kwargs...)

## キーワードパラメータ

  * `point`            - 点サポートでの補間を実行する（デフォルトは `true`）
  * `prob`             - 確率的補間を実行する（デフォルトは `false`）
  * `get_only_weights` - 補間器のデクラスタリング重みのみを取得する
  * `minneighbors`     - 最小隣接数（デフォルトは `1`）
  * `maxneighbors`     - 最大隣接数（デフォルトは `10`）
  * `neighborhood`     - 検索近傍（デフォルトは `nothing`）
  * `local_search`     - ローカル異方性を使用して回転/スケール検索を行うかどうか
