```
nonlocality_robustness(FP::Array; noise::String = "white", verbose::Bool = false, solver = Hypatia.Optimizer{_solver_type(T)})
```

行動 `FP` の非局所性ロバスト性を計算します。引数 `noise` は使用するノイズの種類を示します: "white"（デフォルト）、"local"、または "general"。

参考文献: Baek, Ryu, Lee, [arxiv:2311.07077](https://arxiv.org/abs/2311.07077)
