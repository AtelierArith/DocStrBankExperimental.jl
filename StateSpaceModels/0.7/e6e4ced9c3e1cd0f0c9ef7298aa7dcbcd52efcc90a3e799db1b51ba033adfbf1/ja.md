```
constrain_identity!(model::StateSpaceModel, str::String)
```

制約されたハイパーパラメータ $\psi \in \mathbb{R}$ を制約のないハイパーパラメータ $\psi_* \in \mathbb{R}$ にマッピングします。この関数は、`HyperParameters` 内のある場所から別の場所に値をコピーするために必要です。

マッピングは $\psi = \psi_*$ です。
