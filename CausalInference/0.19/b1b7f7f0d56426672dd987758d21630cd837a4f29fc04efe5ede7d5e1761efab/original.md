```
kwargs_pdag_graphmakie(g; ilabels=1:nv(g), arrowsize=25, ilabels_fontsize=25)
```

Generates the keywords for `GraphMakie.graphplot` to plot causal graphs and (C)PDAGs represented as `SimpleDiGraph` as partially directed graphs.

Usage:

```
graphplot(g; kwargs_pdag_graphmakie(g)...)
```
