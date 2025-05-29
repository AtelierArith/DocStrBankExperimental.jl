```julia
getTreeAllFrontalSyms(_, tree)

```

各クリークから1つのシンボル（フロンタル変数）を`::BayesTree`から返します。

ノート

  * フロンタル変数は、ツリーごとにクリーク内で1回しか発生しないため、ユニークな識別子です。

関連:

whichCliq, printCliqHistorySummary
