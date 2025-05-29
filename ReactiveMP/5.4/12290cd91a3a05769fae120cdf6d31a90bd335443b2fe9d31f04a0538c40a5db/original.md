```
RequireMarginalFunctionalDependencies(specifications::NamedTuple)
RequireMarginalFunctionalDependencies(; specifications...)
```

The same as `DefaultFunctionalDependencies`, but in order to compute a message out of some edge also requires the marginal on the this edge.

The specification parameter is a named tuple that contains the names of the edges and their initial marginals.  When a name is present in the named tuple, that indicates that the computation of the outbound message on the same edge must use the marginal on this edge. If `nothing` is passed as a value in the named tuple, the initial marginal is not set. Note that the construction allows passing keyword argument to the constructor  instead of using `NamedTuple` directly.

```julia
RequireMarginalFunctionalDependencies(μ = vague(NormalMeanPrecision),     τ = nothing)
                                     # ^^^                               ^^^
                                     # request 'marginal' for 'x'        we may do the same for 'τ',
                                     # and initialise with `vague(...)`  but here we skip initialisation
```

See also: [`ReactiveMP.DefaultFunctionalDependencies`](@ref), [`ReactiveMP.RequireMessageFunctionalDependencies`](@ref), [`ReactiveMP.RequireEverythingFunctionalDependencies`](@ref)
