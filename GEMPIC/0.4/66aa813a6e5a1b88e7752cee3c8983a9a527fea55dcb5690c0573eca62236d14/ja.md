```
compute_rhs_from_function(solver, func, component, form)
```

与えられた関数 f と指定された次数の周期スプラインに対して FEM 右辺を計算します。その成分は $\int f N_i dx$ であり、ここで $N_i$ は $x_i$ から始まる B-スプラインです。
