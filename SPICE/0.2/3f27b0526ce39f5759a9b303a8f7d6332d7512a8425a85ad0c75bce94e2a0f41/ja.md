```
ltime(etobs, obs, dir, targ)
```

このルーチンは、指定された観測者での受信（または送信）時間を考慮して、指定されたターゲットでの信号の送信（または受信）時間を計算します。送信と受信の間の経過時間も返されます。

### 引数

  * `etobs`: ある観測者での信号のエポック
  * `obs`: ある観測者のNAIF ID
  * `dir`: 信号が移動する方向（ `"->"` または `"<-"` ）
  * `targ`: 信号の送信と受信の間の時間

### 出力

  * `ettarg`: ターゲットでの信号のエポック
  * `obs`: ある観測者のNAIF ID

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ltime_c.html)
