```
plotsoln(nodes, elements, soln, pyplot)
```

メッシュ上の応力/ひずみをプロットします。solnは要素の数と同じ長さの任意のベクトルである必要があります。例えば、sigma_b[3, :]のように。PyPlotオブジェクトを渡す必要があります。なぜなら、このパッケージではPyPlotがロードされていないからです。
