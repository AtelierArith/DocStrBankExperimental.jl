```
complexgraph(rn::ReactionSystem; complexdata=reactioncomplexes(rn))
```

`rn`内の[`ReactionComplex`](@ref)のGraphvizグラフを作成します。反応は矢印に対応し、反応複合体は青い円に対応します。

注意:

  * 複合体から複合体への黒い矢印は、反応の速度がパラメータまたは`Number`であることを示します。すなわち、`k, A --> B`。
  * 複合体から複合体への赤い破線の矢印は、反応の速度が種に依存することを示します。すなわち、`k*C, A --> B`で`C`は種です。
  * Graphviz jllがインストールされているか、Graphvizがインストールされていてコマンドラインからアクセス可能である必要があります。
