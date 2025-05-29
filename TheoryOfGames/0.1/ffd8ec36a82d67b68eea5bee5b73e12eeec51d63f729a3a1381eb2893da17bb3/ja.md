```
var_least_core(mode, optimizer; verbose)
```

安定した利益分配を計算する関数で、最小コアに属し、プレイヤー間の利益配分の分散を最小化します。これは、効用関数とプレイヤーセットの大連合によって説明されるゲームに対して行われます。

## 入力

mode : EnumMode     計算モード：列挙技術 optimizer : Any     計算目的のために使用されるJuMPモデルの最適化関数 verbose : Bool (オプション、デフォルトはtrue)     trueの場合、現在の実行状況を示すプログレスバーが表示されます

## 出力

specific*least*core_dist : Dict     プレイヤー間の利益の公正な分配の辞書
