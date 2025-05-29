```
RogersYoung <: Closure
```

ロジャース-ヤング閉包を実装します $b(r) = \ln(\frac{\exp(f(r)\gamma(r)) - 1}{f(r)} + 1) - γ(r) $。ここで $f(r)=1-\exp(-\alpha r)$ であり、$\alpha$ は自由パラメータで、熱力学的一貫性が達成されるように選択できます。例:

```julia
closure = RogersYoung(0.5)
```

参考文献:
