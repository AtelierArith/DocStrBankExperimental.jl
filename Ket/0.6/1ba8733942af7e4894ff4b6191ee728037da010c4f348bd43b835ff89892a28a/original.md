```
nonlocality_robustness(FP::Array; noise::String = "white", verbose::Bool = false, solver = Hypatia.Optimizer{_solver_type(T)})
```

Computes the nonlocality robustness of the behaviour `FP`. Argument `noise` indicates the kind of noise to be used: "white" (default), "local", or "general".

Reference: Baek, Ryu, Lee, [arxiv:2311.07077](https://arxiv.org/abs/2311.07077)
