```
unconstrain_variance!(model::StateSpaceModel, str::String)
```

制約のないハイパーパラメータ $\psi_{*} \in \mathbb{R}$ を制約のあるハイパーパラメータ $\psi \in \mathbb{R}^+$ にマッピングします。

マッピングは $\psi_{*} = \sqrt{\psi}$ です。
