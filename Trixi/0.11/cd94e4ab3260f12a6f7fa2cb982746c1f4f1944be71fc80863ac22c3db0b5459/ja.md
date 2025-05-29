```
flux_hllc(u_ll, u_rr, orientation_or_normal_direction, equations::CompressibleEulerEquations2D)
```

圧縮性オイラー方程式に対するHLLCフラックス（接触を伴うHLL）を計算します。E.F. Toroによって開発されました。[講義スライド](http://www.prague-sum.com/download/2012/Toro_2-HLLC-RiemannSolver.pdf) 信号速度: [DOI: 10.1137/S1064827593260140](https://doi.org/10.1137/S1064827593260140)
