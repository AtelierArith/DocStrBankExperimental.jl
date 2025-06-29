```
DebugFeasibility <: DebugAction
```

現在の反復の実現可能性に関する情報を表示します

# フィールド

  * `atol`:   等式または不等式制約が違反と見なされるための絶対許容誤差
  * `format`: 出力をフォーマットするシンボルと文字列のベクター
  * `io`:     デバッグを出力するためのデフォルトストリーム

次のシンボルには値が設定されます

  * `:Feasbile` 反復が実現可能かどうかに応じて真または偽を表示
  * `:FeasbileEq` 等式制約が満たされているかどうかを示す `=` または `≠` を表示
  * `:FeasbileInEq` 不等式制約が満たされているかどうかを示す `≤` または `≰` を表示
  * `:NumEq` 実現不可能な等式制約の数を表示
  * `:NumEqNz` 存在する場合、実現不可能な等式制約の数を表示
  * `:NumIneq` 実現不可能な不等式制約の数を表示
  * `:NumIneqNz` 存在する場合、実現不可能な不等式制約の数を表示
  * `:TotalEq` 等式制約がどれだけ違反されているかの合計を表示
  * `:TotalInEq` 不等式制約がどれだけ違反されているかの合計を表示

出力を印刷するためのフォーマット。

# コンストラクタ

DebugFeasibility(     format=["feasible: ", :Feasible];     io::IO=stdout,     atol=1e-13 )
