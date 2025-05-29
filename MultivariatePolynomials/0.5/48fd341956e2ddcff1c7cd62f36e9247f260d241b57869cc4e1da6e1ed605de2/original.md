```
struct ExponentsIterator{M}(
    object;
    mindegree::Int = 0,
    maxdegree::Union{Nothing,Int} = nothing,
    inline::Bool = false,
)
```

An iterator for generating monomial exponents for monomial ordering `M`. The type of the vector of exponents is the type of `object` and is length (i.e., the number of variables) is `length(object)`.

Note that `object` does not have to be zero, it just needs to implement `copy` and `setindex!` methods (except for `Tuple` which we handle with a special case).

See also [`monomials`](@ref).

### Examples

The following example shows how to generate all exponents of monomials of 2 variables up to degree 2.

```jldoctest
julia> collect(ExponentsIterator{Graded{LexOrder}}((0, 0), maxdegree = 2))
6-element Vector{Tuple{Int64, Int64}}:
 (0, 0)
 (0, 1)
 (1, 0)
 (0, 2)
 (1, 1)
 (2, 0)
```

Note that you can easily generate the tuple of exponents of arbitrary length using `ntuple` as follows:

```jldoctest
julia> collect(ExponentsIterator{Graded{LexOrder}}(ntuple(zero, 3), mindegree = 2, maxdegree = 2))
6-element Vector{Tuple{Int64, Int64, Int64}}:
 (0, 0, 2)
 (0, 1, 1)
 (0, 2, 0)
 (1, 0, 1)
 (1, 1, 0)
 (2, 0, 0)
```

You can also change the monomial ordering and use `Vector` instead of `Tuple` as follows:

```jldoctest
julia> collect(ExponentsIterator{LexOrder}(zeros(Int, 2), mindegree = 2, maxdegree = 3))
7-element Vector{Vector{Int64}}:
 [0, 2]
 [0, 3]
 [1, 1]
 [1, 2]
 [2, 0]
 [2, 1]
 [3, 0]
```
