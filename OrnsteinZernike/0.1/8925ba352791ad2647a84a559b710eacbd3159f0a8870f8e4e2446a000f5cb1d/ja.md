```
ExtendedRogersYoung <: Closure
```

拡張ロジャース-ヤング閉包を実装します $b(r) = \ln(a\phi(r)^2 +  \phi(r) + 1) - γ(r) $。ここで、$\phi(r) = \frac{\exp(f(r)\gamma(r)) - 1}{f(r)}$、および $f(r)=1-\exp(-\alpha r)$ であり、$\alpha$ は自由パラメータで、熱力学的一貫性が達成されるように選択できます。例:

```julia
closure = ExtendedRogersYoung(0.5, 0.5) # 順序は α, a
```

参考文献: J. Chem. Phys. 128, 184507 (2008)
