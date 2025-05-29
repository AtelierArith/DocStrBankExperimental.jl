```
RequireMessageFunctionalDependencies(specifications::NamedTuple)
RequireMessageFunctionalDependencies(; specifications...)
```

The same as `DefaultFunctionalDependencies`, but in order to compute a message out of some edge also requires the inbound message on the this edge.

The specification parameter is a named tuple that contains the names of the edges and their initial messages.  When a name is present in the named tuple, that indicates that the computation of the outbound message on the same edge must use the inbound message. If `nothing` is passed as a value in the named tuple, the initial message is not set. Note that the construction allows passing keyword argument to the constructor  instead of using `NamedTuple` directly.

```julia
RequireMessageFunctionalDependencies(μ = vague(NormalMeanPrecision),     τ = nothing)
                                     # ^^^                               ^^^
                                     # request 'inbound' for 'x'         we may do the same for 'τ',
                                     # and initialise with `vague(...)`  but here we skip initialisation
```

See also: [`ReactiveMP.DefaultFunctionalDependencies`](@ref), [`ReactiveMP.RequireMarginalFunctionalDependencies`](@ref), [`ReactiveMP.RequireEverythingFunctionalDependencies`](@ref)
