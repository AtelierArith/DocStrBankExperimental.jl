```
tspan(fp::AbstractFlowpipe)
```

このフローパイプの時間範囲を返します。

### 入力

  * `fp` – フローパイプ

### 出力

与えられたフローパイプの時間範囲を表す区間。フォールバックは `(tstart(fp), tend(fp))` として計算されます。詳細については `tstart(::AbstractFlowpipe)` および `tend(::AbstractFlowpipe)` を参照してください。
