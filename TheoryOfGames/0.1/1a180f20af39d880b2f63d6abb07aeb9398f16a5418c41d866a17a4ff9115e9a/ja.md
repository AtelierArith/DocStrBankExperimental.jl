```
verify_in_core(profit_dist, mode, optimizer; verbose, utilities)
```

与えられた利益分配がコアに属するかどうかを計算する関数。ゲームは効用関数とプレイヤーセットの大連合によって説明される。

## 入力

mode : EnumMode     計算モード：列挙技術 optimizer : Any     計算目的のために使用されるJuMPモデルの最適化関数 verbose : Bool (オプション、デフォルトはtrue)     trueの場合、現在の実行状況を示すプログレスバーが表示される

## 出力

in*core*dist : Dict     プレイヤー間の利益の公正な分配の辞書
