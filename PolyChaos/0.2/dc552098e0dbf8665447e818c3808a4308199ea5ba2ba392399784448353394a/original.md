**Univariate**

```
evaluate(n::Int,x::Array{<:Real},a::AbstractVector{<:Real},b::AbstractVector{<:Real})
evaluate(n::Int,x::Real,a::AbstractVector{<:Real},b::AbstractVector{<:Real})
evaluate(n::Int,x::AbstractVector{<:Real},op::AbstractOrthoPoly)
evaluate(n::Int,x::Real,op::AbstractOrthoPoly)
```

Evaluate the `n`-th univariate basis polynomial at point(s) `x` The function is multiple-dispatched to facilitate its use with the composite type `AbstractOrthoPoly`

If several basis polynomials (stored in `ns`) are to be evaluated at points `x`, then call

```
evaluate(ns::AbstractVector{<:Int},x::AbstractVector{<:Real},op::AbstractOrthoPoly) = evaluate(ns,x,op.α,op.β)
evaluate(ns::AbstractVector{<:Int},x::Real,op::AbstractOrthoPoly) = evaluate(ns,[x],op)
```

If *all* basis polynomials are to be evaluated at points `x`, then call

```
evaluate(x::AbstractVector{<:Real},op::AbstractOrthoPoly) = evaluate(collect(0:op.deg),x,op)
evaluate(x::Real,op::AbstractOrthoPoly) = evaluate([x],op)
```

which returns an Array of dimensions `(length(x),op.deg+1)`.

!!! note
      * `n` is the degree of the univariate basis polynomial
      * `length(x) = N`, where `N` is the number of points
      * `(a,b)` are the recursion coefficients


**Multivariate**

```
evaluate(n::AbstractVector{<:Int},x::AbstractMatrix{<:Real},a::Vector{<:AbstractVector{<:Real}},b::Vector{<:AbstractVector{<:Real}})
evaluate(n::AbstractVector{<:Int},x::AbstractVector{<:Real},a::Vector{<:AbstractVector{<:Real}},b::Vector{<:AbstractVector{<:Real}})
evaluate(n::AbstractVector{<:Int},x::AbstractMatrix{<:Real},op::MultiOrthoPoly)
evaluate(n::AbstractVector{<:Int},x::AbstractVector{<:Real},op::MultiOrthoPoly)
```

Evaluate the n-th p-variate basis polynomial at point(s) x The function is multiply dispatched to facilitate its use with the composite type `MultiOrthoPoly`

If several basis polynomials are to be evaluated at points `x`, then call

```
evaluate(ind::AbstractMatrix{<:Int},x::AbstractMatrix{<:Real},a::Vector{<:AbstractVector{<:Real}},b::Vector{<:AbstractVector{<:Real}})
evaluate(ind::AbstractMatrix{<:Int},x::AbstractMatrix{<:Real},op::MultiOrthoPoly)
```

where `ind` is a matrix of multi-indices.

If *all* basis polynomials are to be evaluated at points `x`, then call

```
evaluate(x::AbstractMatrix{<:Real},mop::MultiOrthoPoly) = evaluate(mop.ind,x,mop)
```

which returns an array of dimensions `(mop.dim,size(x,1))`.

!!! note
      * `n` is a multi-index
      * `length(n) == p`, i.e. a p-variate basis polynomial
      * `size(x) = (N,p)`, where `N` is the number of points
      * `size(a)==size(b)=p`.

