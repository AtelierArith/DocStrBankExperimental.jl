```
grid_interpolate!(q::Edges{Primal/Dual},dq::EdgeGradient{Primal/Dual})
```

Interpolate the primal (dual) tensor data `dq` to primal (dual) edge positions and hold it in `q`.
