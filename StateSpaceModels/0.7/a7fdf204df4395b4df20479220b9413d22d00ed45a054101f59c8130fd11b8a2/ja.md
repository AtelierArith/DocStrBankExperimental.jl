```
unconstrain_box!(model::StateSpaceModel, str::String, lb::Fl, ub::Fl) where Fl
```

制約のないハイパーパラメータ $\psi_* \in \mathbb{R}$ を制約のあるハイパーパラメータ $\psi \in [lb, ub]$ にマッピングします。

マッピングは次のようになります：$\psi_* = -\ln \frac{ub - lb}{\psi - lb} - 1$
