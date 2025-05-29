混合表現に切り替えるためのフェーズタイプ

# フィールド

  * `name`: フェーズの名前
  * `time_start`: 使用するシミュレーション時間（ここではあまり使われない）
  * `final_measures`: フェーズの最後に行う測定、`measure`および`output`を参照

' `limits` : 最終状態に対する制約

# 例

```
ToMixed()
ToMixed(limits = Limits(cutoff = 1e-10, maxdim = 10))
```
