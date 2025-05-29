```
Surjection{K}

Surjection{K}(u [; check = true]) where K
Surjection(u)

(surj::Surjection)(x::T) where T <: AbstractSimplex -> Linear{T}
```

The type `Surjection{K}` represents elements of arity `K` in the surjection operad.

The first constructor return the surjection given by `u` TODO. If the optional keyword argument `check` is set to `false`, then it is not checked that `u` is indeed a surjection. The second constructor is equivalent to the first with `K` set to `maximum(u; init = 0)`.

When a `Surjection` is applied to a simplex, the result is the corresponding interval cut operation. This evaluation is linear and supports the keyword arguments `coefftype`, `addto`, `coeff` and `is_filtered` as described for the macro `@linear`.

See also [`arity`](@ref), [`deg(::Surjection)`](@ref), [`diff(::Surjection)`](@ref), [`SimplicialSets.is_surjection`](@ref), [`LinearCombinations.linear_filter(::Surjection)`](@ref), `LinearCombinations.@linear`.

# Examples

## Surjection operad

```jldoctest
julia> Surjection([1, 2, 3, 1])
Surjection{3}([1, 2, 3, 1])

julia> Surjection(Int[])
Surjection{0}(Int64[])
```

## Interval cuts

```jldoctest
julia> using LinearCombinations: diff, deg

julia> surj = Surjection([1, 2, 1])
Surjection{2}([1, 2, 1])

julia> x = SymbolicSimplex(:x, 2)
x[0,1,2]

julia> surj(x)
Linear{Tensor{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 3 terms:
-x[0,1,2]⊗x[0,1]-x[0,1,2]⊗x[1,2]+x[0,2]⊗x[0,1,2]

julia> diff(surj(x)) == diff(surj)(x) + (-1)^deg(surj) * surj(diff(x))
true
```
