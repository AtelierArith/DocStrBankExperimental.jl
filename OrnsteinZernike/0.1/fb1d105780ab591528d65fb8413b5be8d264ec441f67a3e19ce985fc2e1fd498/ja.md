```
Verlet <: Closure
```

Verlet閉包を実装します $b(r) = -\frac{A\gamma^2(r)/2}{1+B \gamma(r)/2}$。デフォルトでは$A=1$、$B=8/5$です。これらの値は3次元ハードスフィア液体のビリアル係数によって調整されます。

例:

```julia
closure = Verlet()
closure = Verlet(A=3.0, B=4.0)
```

参考文献:

Verlet, Loup. "Integral equations for classical fluids: I. The hard sphere case." Molecular Physics 41.1 (1980): 183-190.
