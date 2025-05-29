```julia
struct ContIterable{Tkind<:BifurcationKit.AbstractContinuationKind, Tprob, Talg, T, S, E, TnormC, Tfinalisesolution, TcallbackN, Tevent} <: BifurcationKit.AbstractContinuationIterable{Tkind<:BifurcationKit.AbstractContinuationKind}
```

Define a continuation iterator. This allows for example to do:

```
iter = ContIterable(prob, alg, opts; kwargs...)
for state in iter
    println("Continuation step = ", state.step)
end
```

More information is available on the [website](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/iterator/)

# Useful functions

  * `setparam(iter, p::Real)` set parameter with lens `iter.prob.lens` to `p`
  * `is_event_active(iter)` whether the event detection is active
  * `compute_eigenelements(iter)` whether to compute eigen elements
  * `save_eigenvectors(iter)` whether to save eigen vectors
  * `getparams(iter)` get full list of continuation parameters
  * `isindomain(iter, p)` whether `p` in is domain [p*min, p*max]. (See [`ContinuationPar`](@ref))
  * `is_on_boundary(iter, p)` whether `p` in is {p*min, p*max}
