```
ErrmeasureType = Union{Type{<:Errmeasure}, Function}
```

The `ErrmeasureType` represents (essentially) what you can insert in the `errmeasure` keyword argument for most NEP-solvers. It can be a function or an  [`Errmeasure`](@ref) object. If it is a `Function` this function will be used to obtain error estimate.

# Example

This shows how to compute a reference solution and then use this as a reference solution. The error in the second run will be effectively the eigenvector error (appropriately normalized).

```julia
julia> using LinearAlgebra
julia> nep=nep_gallery("qdep0");
julia> (λref,vref)=quasinewton(nep,λ=-1,v=ones(size(nep,1)));
julia> myerrmeasure=(λ,v) -> norm(vref/vref[1]-v/v[1]);
julia> (λ,v)=quasinewton(nep,errmeasure=myerrmeasure,λ=-1.0 ,logger=1,tol=5e-13,v=ones(size(nep,1)));
Precomputing linsolver
iter 1 err:46.40296482739195 λ=-1.0 + 0.0im
iter 2 err:2.1592671533657883 λ=-0.7063330111559607 + 0.0im
iter 3 err:0.17079231439255405 λ=-0.8919579082730457 + 0.0im
iter 4 err:0.1633846991066227 λ=-1.0097584042560848 + 0.0im
iter 5 err:0.003434042059262583 λ=-1.0023823873044 + 0.0im
iter 6 err:0.0003182517281689052 λ=-1.0024660870524031 + 0.0im
iter 7 err:2.0105257231740345e-5 λ=-1.0024677891861997 + 0.0im
iter 8 err:1.618661190265619e-6 λ=-1.0024669496893164 + 0.0im
iter 9 err:1.233489068442819e-7 λ=-1.0024669918249076 + 0.0im
iter 10 err:9.44707811957546e-9 λ=-1.0024669883439166 + 0.0im
iter 11 err:7.867601351698812e-10 λ=-1.0024669886059947 + 0.0im
iter 12 err:0.0 λ=-1.002466988585764 + 0.0im

```

The eigenvalue error can be measured with the [`EigvalReferenceErrmeasure`](@ref).

See also: [`Errmeasure`](@ref)
