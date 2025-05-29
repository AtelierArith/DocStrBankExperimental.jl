```
diamond_norm(
    J::AbstractMatrix,
    dims::AbstractVecOrTuple;
    verbose::Bool = false,
    solver = Hypatia.Optimizer{_solver_type(T)})
```

Choi-Jamiołkowski 表現で与えられたスーパー写像 `J` のダイヤモンドノルムを、サブシステムの次元 `dims` を用いて計算します。

参考文献: [Diamond norm](https://en.wikipedia.org/wiki/Diamond_norm)
