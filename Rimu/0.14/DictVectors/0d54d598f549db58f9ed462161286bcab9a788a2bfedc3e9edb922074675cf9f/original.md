```
Norm1ProjectorPPop() <: AbstractProjector
```

Results in computing the one-norm per population when used in `dot()`. E.g.

```julia
dot(Norm1ProjectorPPop(),x)
-> norm(real.(x),1) + im*norm(imag.(x),1)
```

See also [`PostStepStrategy`](@ref Main.PostStepStrategy), and [`AbstractProjector`](@ref) for use of projectors in [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem).
