```
stable_submodules(T::TorQuadModule, act::Vector{TorQuadModuleMap}; kw...)
```

Return the submodules of `T` stable under the endomorphisms in `act` as an iterator. Possible keyword arguments to restrict the submodules:

  * `quotype::Vector{Int}`: only submodules whose quotient are isomorphic as an abelian group to `abelian_group(quotype)`.
