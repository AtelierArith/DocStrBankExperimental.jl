```
StochasticModel(X, p)
```

Combine stochastic program `X` with parameter `p` into  a trainable model using [Functors](https://fluxml.ai/Functors.jl/stable/), where `p <: AbstractArray`. Formulate as a minimization problem, i.e. find $p$ that minimizes $\mathbb{E}[X(p)]$.
