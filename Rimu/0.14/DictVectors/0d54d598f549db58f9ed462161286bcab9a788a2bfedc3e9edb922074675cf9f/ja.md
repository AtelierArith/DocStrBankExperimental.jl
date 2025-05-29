```
Norm1ProjectorPPop() <: AbstractProjector
```

`dot()`で使用されると、各集団の1ノルムを計算します。例えば、

```julia
dot(Norm1ProjectorPPop(),x)
-> norm(real.(x),1) + im*norm(imag.(x),1)
```

[`PostStepStrategy`](@ref Main.PostStepStrategy)や[`AbstractProjector`](@ref)を参照して、[`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem)におけるプロジェクターの使用方法を確認してください。
