```
covellipse(μ, Σ; showaxes=false, n_std=1, n_ellipse_vertices=100)
```

2×2の共分散行列`Σ`を中心に`μ`で信頼楕円をプロットします。楕円は、平均`μ`と分散`Σ`を持つガウス密度関数の等高線であり、`n_std`標準偏差の位置にあります。`showaxes`がtrueの場合、楕円の2つの軸もプロットされます。
