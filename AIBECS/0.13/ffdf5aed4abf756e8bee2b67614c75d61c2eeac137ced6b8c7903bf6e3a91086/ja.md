```
minimap(grd; central_longitude=200°)
```

grdのサーフスマップをプロットし、目盛り、ラベル、またはカラーバーは表示しません。

この関数の目的は、トランセクトをプロットする際にミニマップとクルーズトラックの両方をプロットする方法を提供することです：

```
plottransect(dummy, grd; ct=sort(ct))
plot!(inset_subplots=bbox(0.73,0.73,0.15,0.15), subplot=2)
minimap!(grd; subplot=2)
plotcruisetrack!(sort(ct), subplot=2)
```
