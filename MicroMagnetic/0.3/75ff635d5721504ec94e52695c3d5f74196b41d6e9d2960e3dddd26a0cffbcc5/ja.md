```
init_m0_skyrmion(sim::AbstractSim, center::Tuple, R::Float64; ratio=0.7, p=-1, c=1, type="B")
```

スカーミオンを用いて磁化を設定します。この関数は、より多くのスカーミオンを追加するために複数回呼び出すことができます。

center : スカーミオンの中心で、タプルである必要があります。例えば、center = (50e-9,50e-9)

R : スカーミオンの半径。

ratio : ratio=w/R で、wはドメイン壁の幅です。デフォルトでは ratio = 0.7 です。

p : 極性、+1 → コア上向き; -1 → コア下向き

c : キラリティ、+1 → 左巻き、正のDの場合; -1 → 右巻き、負のDの場合

type : "B" または "N"、ブロッホまたはニールスカーミオンを表します。

例えば：

```julia
    init_m0_skyrmion(sim, (50e-9,50e-9), 2e-8, ratio=0.5, p=-1, c=1, type="B")
```
