# カプートの分数導関数高次近似

!!! info
    `CaputoHighOrder` メソッドを使用することで、$0<\alpha<2$ を設定できます。


### 例

```julia-repl
julia> fracdiff(x->x, 0.5, 1, 0.01, 2, CaputoHighOrder())
1.1283791670955123
```

```tex
@article{Li2017HighOrderAT,
  title={High-Order Approximation to Caputo Derivatives and Caputo-type Advection–Diffusion Equations: Revisited},
  author={Changpin Li and Minhao Cai},
  journal={Numerical Functional Analysis and Optimization},
  year={2017},
  volume={38},
  pages={861 - 890}
}
```
