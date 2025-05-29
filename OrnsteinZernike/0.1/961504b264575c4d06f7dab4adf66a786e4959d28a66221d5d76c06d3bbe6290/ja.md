```
HardSpheres
```

単一成分系のためのハードスフィアペア相互作用を実装します。$ u(r) = \infty$ は $r < 1$ の場合、$u(r) = 0$ は $r > 1$ の場合、または混合物の場合は $u_{ij}(r) = \infty$ は $r < D_{ij}$ の場合、$u_{ij}(r) = 0$ は $r > D_{ij}$ の場合です。

混合物の場合、各種の直径のベクトル $D_i$ を期待し、その場合は加法的混合則が使用されます $\left(D_{ij} = (D_{i}+D_{j})/2\right)$  またはペア直径の行列 $D_ij$ を期待します。

例:

```example 1
potential = HardSpheres(1.0)
```

例:

```example 2
potential = HardSpheres([0.8, 0.9, 1.0])
```

```example 3
Dij = rand(3,3)
potential = HardSpheres(Dij)
```
