```
Lcurve_functions(Ψ::RegularizationProblem, b̄::AbstractVector, x̄₀::AbstractVector)
```

L-曲線関数を計算して、ノルム L1、L2、および曲率 κ を評価します。ベクトル b̄ と x̄₀ は標準形式である必要があります。

使用例

```julia
Ψ = setupRegularizationProblem(A, 1)
b̄, x̄₀ = to_standard_form(Ψ, b, x₀)                 
L1norm, L2norm, κ = Lcurve_functions(Ψ, b̄, x̄₀)

L1norm.([0.1, 1.0, 10.0])    # λ の L1 ノルム
L2norm.([0.1, 1.0, 10.0])    # λ の L2 ノルム
κ.([0.1, 1.0, 10.0])         # λ の L-曲線曲率
```
