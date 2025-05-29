```
away_frank_wolfe(f, grad!, lmo, x0; ...)
```

Frank-Wolfe with away steps. The algorithm maintains the current iterate as a convex combination of vertices in the [`FrankWolfe.ActiveSet`](@ref) data structure. See [M. Besançon, A. Carderera and S. Pokutta 2021](https://arxiv.org/abs/2104.06675) for illustrations of away steps.
