```
var_least_core(mode, optimizer; verbose)
```

安定した利益分配を計算する関数で、最小コアに属し、プレイヤーセットの効用関数と大連合によって説明されるゲームにおける利益配分の分散を最小化します。

## 入力

mode : EnumMode     計算モード：列挙技術 optimizer : Any     計算目的で使用されるJuMPモデルの最適化関数 numerical_multiplier : Float (デフォルト 1e-3)     数値的問題を調整するための乗数 verbose : Bool (オプション、デフォルト true)     trueの場合、現在の実行状況を示すプログレスバーが表示されます

## 出力

specific*least*core_dist : Dict     プレイヤー間の利益の公正な分配の辞書
