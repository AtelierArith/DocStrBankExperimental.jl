```
specific_least_core(mode, dist_objective, optimizer; verbose, raw_outputs)
```

安定した利益分配を計算する関数で、最小コアに属し、プレイヤー間の利益配分のための特定の目的を最小化します。このゲームは効用関数とプレイヤーセットの大連合によって説明されます。

## 入力

mode : EnumMode     計算モード：列挙技術 dist*objective : Function     最小コアが得られた後の利益分配の目的関数を構築する関数     これは、問題のJuMPモデルとプレイヤーセットの2つの引数を持つ関数であり、     JuMPの@NLobjectiveまたは@objectiveコマンドを使用して、     望ましい目的関数を構築します optimizer : Any     計算目的で使用されるJuMPモデルの最適化関数 verbose : Bool (オプション、デフォルトはtrue)     trueの場合、現在の実行状況を示すプログレスバーを表示します raw*outputs : Bool (オプション、デフォルトはfalse)     trueの場合、すべての生の出力を返します

## 出力

specific*least*core_dist : Dict     プレイヤー間の公正な利益分配の辞書
