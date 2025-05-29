```
constrain_box!(model::StateSpaceModel, str::String, lb::Fl, ub::Fl) where Fl
```

制約付きハイパーパラメータ $\psi \in [lb, ub]$ を制約のないハイパーパラメータ $\psi_* \in \mathbb{R}$ にマッピングします。

マッピングは次のようになります：$\psi = lb + \frac{ub - lb}{1 + \exp(-\psi_{*})}$
