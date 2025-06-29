```
 print_bridge_graph([io::IO,] model::Model)
```

モデルに存在する変数、制約、および目的をブリッジすることによって得られるすべての変数、制約、および目的のタイプを含むハイパーグラフを印刷します。

ハイパーグラフの各ノードは、変数、制約、または目的のタイプに対応しています。

  * 変数ノードは `[ ]` で示されます
  * 制約ノードは `( )` で示されます
  * 目的ノードは `| |` で示されます

各ブラケットの中の数字は、ハイパーグラフ内のノードのインデックスです。

このハイパーグラフは、可能な変換の完全なリストであることに注意してください。ブリッジされたモデルが作成されるとき、私たちはこのグラフから最短のハイパーパスを選択するため、多くのノードが未使用のままになる可能性があります。

詳細については、Legat, B., Dowson, O., Garcia, J., and Lubin, M. (2020).  "MathOptInterface: a data structure for mathematical optimization problems." URL: [https://arxiv.org/abs/2002.03447](https://arxiv.org/abs/2002.03447)をご覧ください。
