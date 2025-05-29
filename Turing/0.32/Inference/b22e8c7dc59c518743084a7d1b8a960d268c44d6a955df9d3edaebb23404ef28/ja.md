```
SGLD(
    space::Symbol...;
    stepsize = PolynomialStepsize(0.01),
    adtype::ADTypes.AbstractADType = AutoForwardDiff(),
)
```

確率的勾配ランジュバン動力学 (SGLD) サンプラー。

デフォルトでは、多項式的に減衰するステップサイズが使用されます。

自動微分 (AD) バックエンド `adtype` が提供されていない場合、ForwardDiff が自動的に決定された `chunksize` で使用されます。

# 参考文献

Max Welling & Yee Whye Teh (2011). Bayesian Learning via Stochastic Gradient Langevin Dynamics. In: Proceedings of the 28th International Conference on Machine Learning (pp. 681–688).

See also: [`PolynomialStepsize`](@ref)
