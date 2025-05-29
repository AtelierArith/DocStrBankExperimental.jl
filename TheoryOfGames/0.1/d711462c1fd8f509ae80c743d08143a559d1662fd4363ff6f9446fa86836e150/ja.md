```
ref_least_core(mode, ref_dist, optimizer; norm, verbose)
```

安定した利益分配を計算する関数で、最小コアに属し、プレイヤー間の利益配分の分散を最小化します。これは、効用関数とプレイヤーセットの大連合によって説明されるゲームのための事前定義された報酬分配関数に関して行われます。

## 入力

mode : AbstractCalcMode     計算モード：列挙技術 ref_dist : AbstrctDict     プレイヤーによる参照分配 optimizer : Any     計算目的のために使用されるJuMPモデルの最適化関数 norm (オプション、デフォルトは何も指定しない)     各プレイヤーの正規化分母     デフォルト値は何も指定しないため、各プレイヤーの正規化     因子は1.0です verbose : Bool (オプション、デフォルトはtrue)     trueの場合、現在の実行状況を示すプログレスバーを表示します

## 出力

specific*least*core_dist : Dict     プレイヤー間の利益の公正な分配の辞書
