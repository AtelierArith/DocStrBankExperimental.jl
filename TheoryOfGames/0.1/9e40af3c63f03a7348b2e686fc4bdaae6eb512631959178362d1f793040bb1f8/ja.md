```
in_core(mode, optimizer; verbose, raw_outputs)
```

コアに属する安定した利益分配を計算する関数で、効用関数とプレイヤーセットの大連合によって説明されるゲームの利益分配のためのものです。

## 入力

mode : EnumMode     計算モード：列挙技術 optimizer : Any     計算目的のために使用されるJuMPモデルの最適化関数 verbose : Bool (オプション、デフォルトはtrue)     trueの場合、現在の実行状況を示すプログレスバーが表示されます

## 出力

in*core*dist : Dict     プレイヤー間の利益の公正な分配の辞書
