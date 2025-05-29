```
var_in_core(mode, optimizer; verbose)
```

コアに属し、プレイヤー間の利益配分の分散を最小化する安定した利益分配を計算する関数で、効用関数とプレイヤーセットの大連合によって説明されるゲームに関連しています。

## 入力

mode : EnumMode     計算モード：列挙技術 optimizer : Any     計算目的のために使用されるJuMPモデルの最適化関数 verbose : Bool (オプション、デフォルトはtrue)     trueの場合、現在の実行状況を示すプログレスバーが表示されます

## 出力

var_core : Dict     プレイヤー間の公正な利益分配の辞書
