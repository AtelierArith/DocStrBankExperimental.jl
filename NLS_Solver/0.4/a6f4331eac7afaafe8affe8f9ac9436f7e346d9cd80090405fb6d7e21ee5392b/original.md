Store bound constraints $[l,u]$

Presence of `NaN` component and the $l\le u$ condition is checked at construction time. Note however that some components can be infinite.

# Constructors

The following constructors are available:

  * Construct $[0.0,1.0]^n$

```julia
BoundConstraints(n)
```

  * Construct $[T(0),T(1)]^n$ where components are of type `T`

```julia
BoundConstraints(T,n)
```

  * Construct $[l,u]$ where `l` and `u` are lower and upper bound vectors

```julia
BoundConstraints(l,u)
```

# Related functions

  * [`Base.eltype(bc::BoundConstraints{ELT}) where ELT`](@ref)
  * [`Base.axes(bc::BoundConstraints)`](@ref)
  * [`Base.length(bc::BoundConstraints)`](@ref)
  * [`Base.size(bc::BoundConstraints)`](@ref)
  * [`in(x::AbstractArray{<:Real,N},bc::BoundConstraints{<:Real,N}) where N`](@ref)
  * [`lower_bound(bc::BoundConstraints)`](@ref)
  * [`upper_bound(bc::BoundConstraints)`](@ref)
  * [`project!(x::AbstractArray{<:Real,N},bc::BoundConstraints{<:Real,N}) where N`](@ref)
  * [`Base.:-(bc::BoundConstraints,τ::AbstractArray)`](@ref)
  * [`Base.:+(bc::BoundConstraints,τ::AbstractArray)`](@ref)
