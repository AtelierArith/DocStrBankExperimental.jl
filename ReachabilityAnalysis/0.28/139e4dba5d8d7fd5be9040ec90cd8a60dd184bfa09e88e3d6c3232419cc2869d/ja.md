```
ShiftedFlowpipe{FT<:AbstractFlowpipe, NT<:Number} <: AbstractFlowpipe
```

時間的にシフトされたフローパイプを遅延的に表現する型です。

### フィールド

  * `F`  – 元のフローパイプ
  * `t0` – 時間シフト

### 注意事項

この型は `AbstractFlowpipe` の任意の具体的なサブタイプをラップすることができ、追加のフィールド `t0` は `F` の各リーチセットの時間範囲が `t0` の量だけシフトされるようになっています（`Number` のサブタイプであるべきです）。
