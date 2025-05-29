```
diamond_norm(
    J::AbstractMatrix,
    dims::AbstractVecOrTuple;
    verbose::Bool = false,
    solver = Hypatia.Optimizer{_solver_type(T)})
```

Computes the diamond norm of the supermap `J` given in the Choi-Jamiołkowski representation, with subsystem dimensions `dims`.

Reference: [Diamond norm](https://en.wikipedia.org/wiki/Diamond_norm)
