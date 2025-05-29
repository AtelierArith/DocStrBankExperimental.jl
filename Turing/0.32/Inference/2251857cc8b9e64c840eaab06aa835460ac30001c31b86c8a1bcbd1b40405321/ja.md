```
SGHMC(
    space::Symbol...;
    learning_rate::Real,
    momentum_decay::Real,
    adtype::ADTypes.AbstractADType = AutoForwardDiff(),
)
```

確率的勾配ハミルトニアンモンテカルロ（SGHMC）サンプラーを作成します。

自動微分（AD）バックエンド `adtype` が提供されていない場合、ForwardDiff が自動的に決定された `chunksize` で使用されます。

# 参考文献

Tianqi Chen, Emily Fox, & Carlos Guestrin (2014). Stochastic Gradient Hamiltonian Monte Carlo. In: Proceedings of the 31st International Conference on Machine Learning (pp. 1683–1691).
