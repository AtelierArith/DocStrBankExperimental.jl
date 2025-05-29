```
NormProjector() <: AbstractProjector
```

`dot()`で使用されるときに1ノルムを計算する結果になります。例えば、

```julia
dot(NormProjector(),x)
-> norm(x,1)
```

したがって、`NormProjector()`はベクトル`sign.(x)`を表します。

[`PostStepStrategy`](@ref Main.PostStepStrategy)や[`AbstractProjector`](@ref)を参照して、[`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem)におけるプロジェクターの使用方法を確認してください。
