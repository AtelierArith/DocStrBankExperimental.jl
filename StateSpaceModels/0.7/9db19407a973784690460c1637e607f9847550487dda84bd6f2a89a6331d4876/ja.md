```
constrain_variance!(model::StateSpaceModel, str::String)
```

制約されたハイパーパラメータ $\psi \in \mathbb{R}^+$ を制約のないハイパーパラメータ $\psi_* \in \mathbb{R}$ にマッピングします。

マッピングは $\psi = \psi_*^2$ です。
