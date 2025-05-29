```julia
ForwardDiffOverAdjoint{A} <: AbstractSecondOrderSensitivityAlgorithm{nothing, true, nothing}
```

ForwardDiff.jl の選択された `sensealg` メソッドに対するアジョイント。

## コンストラクタ

```julia
ForwardDiffOverAdjoint(sensealg)
```

## SciMLProblem サポート

これは、ソルバーアルゴリズムが `SciMLBase.isautodifferentiable` である限り、`sensealg` の選択がサポートする任意の SciMLProblem をサポートします。

## 参考文献

Hindmarsh, A. C. and Brown, P. N. and Grant, K. E. and Lee, S. L. and Serban, R. and Shumaker, D. E. and Woodward, C. S., SUNDIALS: Suite of nonlinear and differential/algebraic equation solvers, ACM Transactions on Mathematical Software (TOMS), 31, pp:363–396 (2005)
