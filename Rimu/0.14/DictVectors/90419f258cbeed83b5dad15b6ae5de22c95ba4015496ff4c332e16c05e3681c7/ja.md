```
Norm2Projector() <: AbstractProjector
```

`dot()`で使用されるときに二乗ノルムを計算します。例えば、

```julia
dot(NormProjector(),x)
-> norm(x,2) # 型は Float64
```

プロジェクターの使用については、[`PostStepStrategy`](@ref Main.PostStepStrategy)や[`AbstractProjector`](@ref)、および[`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem)を参照してください。
