```
least_core(mode, utilities, optimizer; verbose, raw_outputs)
```

ゲームの効用関数とプレイヤーセットの大連合によって記述される最小コアの利益分配を計算する関数。

## 入力

mode : EnumMode     計算モード：列挙技術 player*set : Vector     連合のプレイヤーのベクター optimizer : Any     計算目的で使用されるJuMPモデルの最適化関数 verbose : Bool (オプション、デフォルトはtrue)     trueの場合、現在の実行状況を示すプログレスバーを表示 raw*outputs : Bool (オプション、デフォルトはfalse)     trueの場合、すべての生の出力を返す

## 出力

leastcore_dist : Dict     プレイヤー間の利益の公正な分配の辞書
