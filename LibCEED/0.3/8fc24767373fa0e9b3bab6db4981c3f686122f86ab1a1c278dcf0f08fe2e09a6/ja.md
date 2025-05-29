```
apply_add!(op::Operator, vin, vout; request=RequestImmediate())
```

演算子 `op` の作用を入力ベクトル `vin` に適用し、その結果を出力ベクトル `vout` に加えます。

非ブロッキングの適用の場合、ユーザーはリクエストオブジェクトを指定できます。デフォルトでは、即時（同期的）な完了が要求されます。
