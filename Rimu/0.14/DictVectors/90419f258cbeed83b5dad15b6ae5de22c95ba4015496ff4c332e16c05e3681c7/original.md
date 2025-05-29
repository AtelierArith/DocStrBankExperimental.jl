```
Norm2Projector() <: AbstractProjector
```

Results in computing the two-norm when used in `dot()`. E.g.

```julia
dot(NormProjector(),x)
-> norm(x,2) # with type Float64
```

See also [`PostStepStrategy`](@ref Main.PostStepStrategy), and [`AbstractProjector`](@ref) for use of projectors in [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem).
