```
ModifiedVerlet <: Closure
```

修正されたVerlet閉包を実装します $b(r) = -\frac{\gamma^2(r)/2}{1+\alpha \gamma(r)}$。もし $\gamma(r)<0$ の場合、閉包は $-\gamma^2/2$ となります。例:

```julia
closure = ModifiedVerlet(0.2)
```

参考文献:

Verlet, Loup. "Integral equations for classical fluids: I. The hard sphere case." Molecular Physics 41.1 (1980): 183-190.
