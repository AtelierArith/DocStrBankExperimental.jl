```
boxdot(A,B) = A ⊡ B    # \boxdot
```

Generalised matrix multiplication: Contracts the last dimension of `A` with the first dimension of `B`, for any `ndims(A)` & `ndims(B)`. If both are vectors, then it returns a scalar `== sum(A .* B)`.

# Examples

```jldoctest; setup=:(using TensorCore)
julia> A = rand(3,4,5); B = rand(5,6,7);

julia> size(A ⊡ B)
(3, 4, 6, 7)

julia> typeof(rand(5) ⊡ rand(5))
Float64

julia> try B ⊡ A catch err println(err) end
DimensionMismatch("neighbouring axes of `A` and `B` must match, got Base.OneTo(7) and Base.OneTo(3)")
```

This is the same behaviour as Mathematica's function `Dot[A, B]`. It is not identicaly to Python's `numpy.dot(A, B)`, which contracts with the second-last dimension of `B` instead of the first, but both keep all the other dimensions. Unlike Julia's `LinearAlgebra.dot`, it does not conjugate `A`, so these two agree only for real-valued vectors.

When interacting with `Adjoint` vectors, this always obeys `(x ⊡ y)' == y' ⊡ x'`, and hence may sometimes return another `Adjoint` vector. (And similarly for `Transpose`.)

```jldoctest; setup=:(using TensorCore)
julia> M = rand(5,5); v = rand(5);

julia> typeof(v ⊡ M')
Array{Float64,1}

julia> typeof(M ⊡ v')  # adjoint of the previous line
Adjoint{Float64,Array{Float64,1}}

julia> typeof(v' ⊡ M')  # same as *, and equal to adjoint(M ⊡ v)
Adjoint{Float64,Array{Float64,1}}

julia> typeof(v' ⊡ v)
Float64
```

See also `boxdot!(Y,A,B)`, which is to `⊡` as `mul!` is to `*`.
