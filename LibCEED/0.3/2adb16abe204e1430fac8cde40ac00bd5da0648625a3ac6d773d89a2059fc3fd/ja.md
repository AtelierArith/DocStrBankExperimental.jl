```
apply!(op::Operator, vin, vout; request=RequestImmediate())
```

演算子 `op` の作用を入力ベクトル `vin` に適用し、結果を出力ベクトル `vout` に格納します。

非ブロッキングの適用の場合、ユーザーはリクエストオブジェクトを指定できます。デフォルトでは、即時（同期）完了が要求されます。
