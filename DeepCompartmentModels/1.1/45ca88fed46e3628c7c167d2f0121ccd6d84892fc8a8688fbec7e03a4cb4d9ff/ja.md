```
generate_dosing_callback(I; S1)
```

介入行列 `I` における投与イベントを実装する DiscreteCallback を返します。

# 引数

  * `I`: 時間、投与量、速度、および持続時間の列を含むイベントを持つ行を持つ行列。
  * `S1`: 投与量のスケーリングファクター。モデルパラメータと同じ単位で投与量を取得するために使用されます。デフォルト = 1。
