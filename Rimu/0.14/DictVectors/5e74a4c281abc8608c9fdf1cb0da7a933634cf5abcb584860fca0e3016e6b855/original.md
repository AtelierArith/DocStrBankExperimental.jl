```
NormProjector() <: AbstractProjector
```

Results in computing the one-norm when used in `dot()`. E.g.

```julia
dot(NormProjector(),x)
-> norm(x,1)
```

`NormProjector()` thus represents the vector `sign.(x)`.

See also [`PostStepStrategy`](@ref Main.PostStepStrategy), and [`AbstractProjector`](@ref) for use of projectors in [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem).
