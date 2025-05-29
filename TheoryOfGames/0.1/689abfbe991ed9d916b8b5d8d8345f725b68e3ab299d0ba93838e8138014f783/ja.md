```
ref_in_core(mode, ref_dist, optimizer; verbose)
```

コアに属し、プレイヤー間の利益配分の分散を最小化する安定した利益分配を計算する関数で、効用関数とプレイヤーセットの大連合によって説明されるゲームのための事前定義された報酬分配関数に関しています。

## 入力

mode : IterMode     計算モード：列挙技術 ref*dist : AbstrctDict     プレイヤーによる参照分配 optimizer : Any     計算目的のために使用されるJuMPモデルの最適化関数 norm : Any     各プレイヤーの正規化分母     デフォルト値はnothingであり、したがって各プレイヤーの正規化     ファクターは1.0です numerical*multiplier : Float (default 1e-3)     数値的問題を調整するための乗数 verbose : Bool (optional, default true)     trueの場合、現在の実行状況を説明するプログレスバーを表示します

## 出力

specific*ref*in*core*dist : Dict     プレイヤー間の公正な利益分配の辞書
