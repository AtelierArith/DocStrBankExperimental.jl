```
likelihood(events::Array{<:Number, 1}, background::Float64, kappa::Float64, kernel::Distributions.Distribution, maxT::Number)
```

与えられたパラメータに対するホークス過程の対数尤度を計算します。

# 引数

  * `events` 尤度を計算するためのイベントのベクター。
  * `background` バックグラウンドレート。
  * `kappa` カッパパラメータ。
  * `kernel` カーネルの関数または分布。
  * `maxT` プロセスの最大時間。

# 注意事項

  * カーネル関数は適切な確率分布でなければなりません。

# 例

```
