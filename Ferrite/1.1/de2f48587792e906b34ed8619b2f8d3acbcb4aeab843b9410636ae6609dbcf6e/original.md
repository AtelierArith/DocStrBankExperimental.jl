```
QuadratureRule{shape}([::Type{T},] [quad_rule_type::Symbol,] order::Int)
QuadratureRule{shape}(weights::AbstractVector{T}, points::AbstractVector{Vec{rdim, T}})
```

Create a `QuadratureRule` used for integration on the refshape `shape` (of type [`AbstractRefShape`](@ref)). `order` is the order of the quadrature rule. `quad_rule_type` is an optional argument determining the type of quadrature rule, currently the `:legendre` and `:lobatto` rules are implemented for hypercubes. For triangles up to order 8 the default rule is the one by `:dunavant` (see [Dun:1985:hde](@cite)) and for tetrahedra the default rule is `keast_minimal` (see [Keast:1986:mtq](@cite)). Wedges and pyramids default to `:polyquad` (see [WitVin:2015:isq](@cite)). Furthermore we have implemented

  * `:gaussjacobi` for triangles (order 9-15)
  * `:keast_minimal` (see [Keast:1986:mtq](@cite)) for tetrahedra (order 1-5), containing negative weights
  * `:keast_positive` (see [Keast:1986:mtq](@cite)) for tetrahedra (order 1-5), containing only positive weights

A `QuadratureRule` is used to approximate an integral on a domain by a weighted sum of function values at specific points:

$\int\limits_\Omega f(\mathbf{x}) \text{d} \Omega \approx \sum\limits_{q = 1}^{n_q} f(\mathbf{x}_q) w_q$

The quadrature rule consists of $n_q$ points in space $\mathbf{x}_q$ with corresponding weights $w_q$.

In Ferrite, the `QuadratureRule` type is mostly used as one of the components to create [`CellValues`](@ref).

**Common methods:**

  * [`getpoints`](@ref) : the points of the quadrature rule
  * [`getweights`](@ref) : the weights of the quadrature rule

**Example:**

```jldoctest
julia> qr = QuadratureRule{RefTriangle}(1)
QuadratureRule{RefTriangle, Float64, 2}([0.5], Vec{2, Float64}[[0.33333333333333, 0.33333333333333]])

julia> getpoints(qr)
1-element Vector{Vec{2, Float64}}:
 [0.33333333333333, 0.33333333333333]
```
