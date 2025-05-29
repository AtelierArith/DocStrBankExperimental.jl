```
evolve!(::Stencil,φ,vel,Δt,Δx,isperiodic,caches) -> φ
```

与えられた `Stencil` に対するハミルトン・ヤコビ進化方程式の単一有限差分ステップ。
