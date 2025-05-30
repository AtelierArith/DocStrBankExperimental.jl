```
kwargs_pdag_graphmakie(g; ilabels=1:nv(g), arrowsize=25, ilabels_fontsize=25)
```

`GraphMakie.graphplot` に渡すためのキーワードを生成し、`SimpleDiGraph` として表現された因果グラフおよび (C)PDAG を部分的に指向されたグラフとしてプロットします。

使用法:

```
graphplot(g; kwargs_pdag_graphmakie(g)...)
```
