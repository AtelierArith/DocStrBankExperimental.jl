```
BallonePastoreGalliGazzillo <: Closure
```

Ballone-Pastore-Galli-Gazzillo閉包を実装します $b(r) = (1 + s \gamma(r))^{1/s} - \gamma(r) - 1 $。ここで、$s:は熱力学的一貫性によって決定できる自由パラメータです。

例:

```julia
closure = BallonePastoreGalliGazzillo(1.5)
```

参考文献:

Ballone, P., et al. "Additive and non-additive hard sphere mixtures: Monte Carlo simulation and integral equation results." Molecular Physics 59.2 (1986): 275-290.
