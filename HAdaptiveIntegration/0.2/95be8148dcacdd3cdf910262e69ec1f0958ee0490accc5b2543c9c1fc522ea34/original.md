```
integrate(
    fct,
    domain::AbstractDomain{D,T};
    embedded_cubature::EmbeddedCubature{D,T}=default_embedded_cubature(domain),
    subdiv_algo=default_subdivision(domain),
    buffer=nothing,
    norm=x -> LinearAlgebra.norm(x, Inf),
    atol=zero(T),
    rtol=(atol > zero(T)) ? zero(T) : sqrt(eps(T)),
    maxsubdiv=8192 * 2^D,
) where {D,T}
```

Return `I` and `E` where `I` is the integral of the function `fct` over `domain` and `E` is an error estimate.

## Arguments

  * `fct`: a function that must take a `SVector{D,T}` to a return type `K`, with `K` must  support the multiplication by a scalar of type `T` and the addition.
  * `domain::AbstractDomain{D,T}`: the integration domain. Currently, we support [`Triangle`](@ref), [`Rectangle`](@ref), [`Tetrahedron`](@ref), [`Cuboid`](@ref), `d`-dimensional [`Simplex`](@ref), and `d`-dimensional [`Orthotope`](@ref).

## Optional arguments

  * `embedded_cubature::EmbeddedCubature{D,T}=default_embedded_cubature(domain)`: the embedded cubature,  each supported domain has a [`default_embedded_cubature`](@ref).
  * `subdiv_algo=default_subdivision(domain)`: the subdivision algorithm, each domain has a [`default_subdivision`](@ref).
  * `buffer=nothing`: heap use to do the adaptive algorithm, can be allocated using  [`allocate_buffer`](@ref), which might result in performance gain if multiple call to  integrate is perform.
  * `norm=x -> LinearAlgebra.norm(x, Inf)`: norm used to estimate the error.
  * `atol=zero(T)`: absolute tolerance.
  * `rtol=(atol > zero(T)) ? zero(T) : sqrt(eps(T))`: relative tolerance.
  * `maxsubdiv=8192 * 2^D`: maximum number of subdivision.
