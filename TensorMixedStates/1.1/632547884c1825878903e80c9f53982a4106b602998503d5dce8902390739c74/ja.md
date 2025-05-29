ゲートを適用するためのフェーズタイプ

  * `name`: フェーズの名前
  * `time_start`: フェーズの開始時に使用するシミュレーション時間
  * `final_measures`: フェーズの終了時に行う測定、`measure`および`output`を参照
  * `limits`: 計算の各ステップで強制する制約
  * `gates`: 適用するゲート

# 例

```
Gates(gates = CNOT(1, 3)*CZ(2,4), limits = Limits(cutoff=1e-10, maxdim = 20))
```
