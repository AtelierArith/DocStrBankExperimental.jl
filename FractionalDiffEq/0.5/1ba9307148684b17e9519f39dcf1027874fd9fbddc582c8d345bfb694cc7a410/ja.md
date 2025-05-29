```
FDDEMatrixProblem(α, τ, A, B, f, x0, tspan)
```

遅延を伴う分数行列微分方程式を一般形で構築します：

$$
D_{t_0}^\alpha\textbf{x}(t)=\textbf{A}(t)\textbf{x}(t)+\textbf{B}(t)\textbf{x}(t-\tau)+\textbf{f}(t)
$$
