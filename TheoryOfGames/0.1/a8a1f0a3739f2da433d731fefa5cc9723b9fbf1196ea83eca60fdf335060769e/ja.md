```
ref_in_core(mode, ref_dist, optimizer; verbose)
```

コアに属し、プレイヤー間の利益配分の分散を最小化する安定した利益分配を計算する関数で、効用関数とプレイヤーセットの大連合によって説明されるゲームのための事前定義された報酬分配関数に関しています。

## 入力

mode : EnumMode     計算モード：列挙技術 ref_dist : AbstrctDict     プレイヤーによる参照分配 optimizer : Any     計算目的のために使用されるJuMPモデルの最適化関数 norm : Any     各プレイヤーの正規化分母     デフォルト値は何も指定されていないため、各プレイヤーの正規化     因子は1.0です verbose : Bool (オプション、デフォルトはtrue)     trueの場合、現在の実行状況を示すプログレスバーが表示されます

## 出力

specific*ref*in*core*dist : Dict     プレイヤー間の利益の公正な分配の辞書
