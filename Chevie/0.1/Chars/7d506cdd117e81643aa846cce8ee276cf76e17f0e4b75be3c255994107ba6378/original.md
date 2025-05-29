`fakedegree(W, φ, q=Pol())`

returns the fake degree (see [`fakedegrees`](@ref) for a definition) of the character  of parameter φ (see  `charinfo(W).charparams`) of the reflection group `W`, evaluated at `q` .

```julia-repl
julia> fakedegree(coxgroup(:A,2),[[2,1]],Pol(:q))
Pol{Int64}: q²+q
```
