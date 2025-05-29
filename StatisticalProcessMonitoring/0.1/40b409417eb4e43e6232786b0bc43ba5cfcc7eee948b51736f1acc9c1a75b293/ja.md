```
run_sim_oc(CH::AbstractChart; shift = 0.0)
```

制御チャート `CH` のために位置シフトの下での実行長をシミュレートし、Phase II オブジェクトから新しいデータをサンプリングします。

### 入力

  * `CH::AbstractChart`:  制御チャート。
  * `shift::Float64` - 位置シフトの大きさ。

### 返り値

  * シミュレートされた実行長を表す `Int`。
