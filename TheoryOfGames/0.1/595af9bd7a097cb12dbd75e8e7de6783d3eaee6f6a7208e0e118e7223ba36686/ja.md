```
nucleolus(mode, utilities; verbose, tol, raw_outputs)
```

ゲームの効用関数とプレイヤーセットの大連合によって説明される核の利益分配を計算する関数。

## 入力

mode : EnumMode     計算モード：列挙技術 optimizer : Any     計算目的のために使用されるJuMPモデルの最適化関数 verbose : Bool (オプション、デフォルトはtrue)     trueの場合、現在の実行状況を示すプログレスバーを表示します tol (オプション、デフォルトは1e-5)     最適化手続きにおけるアクティブな制約を特定するための許容誤差 raw_outputs : Bool (オプション、デフォルトはfalse)     trueの場合、すべての生の出力を返します

## 出力

nucleolus_dist : Dict     プレイヤー間の利益の公正な分配の辞書
