```
specific_in_core(mode, dist_objective, optimizer; verbose, raw_outputs)
```

コアに属し、プレイヤーセットの効用関数と大連合によって記述されたゲームのために指定された特定の分配目的を最大化する安定した利益分配を計算する関数です。

## 入力

mode : EnumMode     計算モード：列挙技術 dist*objective : Function     利益分配の目的関数を構築するための関数     JuMPモデルとプレイヤーセットの2つの引数を持つ関数である必要があります。     そして、JuMPの @NLobjective または @objective     コマンドを使用して目的関数を構築する必要があります。 optimizer : Any     計算目的で使用されるJuMPモデルの最適化関数 verbose : Bool (オプション、デフォルトはtrue)     trueの場合、現在の実行状況を示すプログレスバーを表示します raw*outputs : Bool (オプション、デフォルトはfalse)     trueの場合、すべての生の出力を返します

## 出力

specific*in*core_dist : Dict     プレイヤー間の公正な利益分配の辞書
