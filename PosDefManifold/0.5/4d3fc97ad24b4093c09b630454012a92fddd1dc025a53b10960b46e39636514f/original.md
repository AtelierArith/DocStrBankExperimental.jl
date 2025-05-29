```
    randEigvals(n::Int;
    <
    df::Int=2,
    eigvalsSNR::Real=10e3 >)
```

**alias**: `randλ`

Generate an $n$-vector of random real positive eigenvalues.  The eigenvalues are generated as in function `randΛ`([`randEigvalsMat`](@ref)),  the syntax of which is used.

**See also**: `randU` ([`randUnitaryMat`](@ref)), `randP` ([`randPosDefMat`](@ref)).

**Examples**

```julia
using Plots, PosDefManifold
λ=sort(randλ(10), rev=true)
σ=sort(randλ(10, eigvalsSNR=10), rev=true)
plot(λ) # needs Plots package. Check your plots back-end.
plot!(σ) # needs Plots package. Check your plots back-end.
```
