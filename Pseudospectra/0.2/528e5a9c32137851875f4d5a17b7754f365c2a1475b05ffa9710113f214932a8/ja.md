```
setpsplotter(plotter::Symbol=:default)
```

擬似スペクトルと一緒に使用するプロットパッケージを選択します。

現在、`:Plots` と `:PyPlot` が実装されています。Plotsがインポートされていない場合は、デフォルトで `:Plots` になります。
