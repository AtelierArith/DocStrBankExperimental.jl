```
UniformProjector() <: AbstractProjector
```

すべての要素が1のベクトルを表します。[`dot()`](@ref)と一緒に使用します。メモリの割り当てを最小限に抑えます。

```julia
UniformProjector()⋅v == sum(v)
dot(UniformProjector(), LO, v) == sum(LO*v)
```

プロジェクターの使用については、[`PostStepStrategy`](@ref Main.PostStepStrategy)および[`AbstractProjector`](@ref)を参照してください。[`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem)でのプロジェクターの使用についても参照してください。
