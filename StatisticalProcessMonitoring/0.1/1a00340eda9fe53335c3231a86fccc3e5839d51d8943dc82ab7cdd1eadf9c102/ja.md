```
run_sim(CH::AbstractChart, DGP::AbstractPhase2)
```

制御チャート `CH` のために、提供されたデータ生成プロセス `DGP` から新しいデータをサンプリングすることによって、実行長をシミュレートします。

### 入力

  * `CH` - 制御チャート。
  * `DGP` - AbstractPhase2 オブジェクト。

### 戻り値

  * シミュレートされた実行長を表す `Int`。
