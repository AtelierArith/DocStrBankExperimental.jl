```
mtxexpsplot(ps_data,dt=0.1,nmax=50; gs::GUIState = defaultgs(), gradual=false)
```

`∥e^(tA)∥`の進化をプロットします。

これは線形初期値問題`∂x/∂t = Ax`を分析するのに役立ちます。
