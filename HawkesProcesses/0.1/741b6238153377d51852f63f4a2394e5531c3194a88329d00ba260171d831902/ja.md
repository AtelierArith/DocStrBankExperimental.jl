```
compensator(ts::Number, events::Array{<:Number}, bg::Number, kappa::Number, kern::Distributions.Distribution)
```

補償器または統合強度関数。

# 引数

  * `ts::Number` 統合強度関数を評価する時間。
  * `events::Array{<:Number}` 強度関数からのイベント。
  * `bg::Number` 背景率。
  * `kappa::Number` カッパパラメータ
  * `kern::Distributions.Distribution` カーネルの分布。

# 例
