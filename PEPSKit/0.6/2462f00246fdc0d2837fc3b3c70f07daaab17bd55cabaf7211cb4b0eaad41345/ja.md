```
pwave_superconductor([T=ComplexF64,] lattice::InfiniteSquare; t=1, μ=2, Δ=1)
```

正方格格子$p$波超伝導体モデルは、ハミルトニアンによって定義されます。

$$
    H = -\sum_{\langle i,j \rangle} \left( t c_i^\dagger c_j +
    \Delta c_i c_j + \text{h.c.} \right) - \mu \sum_i n_i,
$$

ここで、$t$はホッピング振幅、$\Delta$は超伝導ギャップを指定し、$\mu$は化学ポテンシャル、$n_i = c_i^\dagger c_i$はフェルミオン数演算子です。
