```
normalize1!(A::AbstractArray{<:Real})
```

Normalize the values in `A` such that `sum(A) ≈ 1` and `0 ≤ A[i] ≤ 1` ∀i. This is not quite the L¹-norm, which would require that `abs(A[i])` be used. It is assumed that `0 ≤ A[i] < Inf` ∀i. `Inf` values are not handled and will result in `NaN`'s.

See also: [`normalize1`](@ref)

```jldoctest
julia> normalize1!([1.0, 2.0, 3.0])
3-element Vector{Float64}:
 0.16666666666666666
 0.3333333333333333
 0.5

julia> normalize1!([1.0, 2.0, Inf])
3-element Vector{Float64}:
   0.0
   0.0
 NaN

julia> normalize1!([1.0, 2.0, NaN])     # NaN propagates, as expected
3-element Vector{Float64}:
 NaN
 NaN
 NaN

julia> normalize1!([1.0, -2.0, 3.0])    # not the L¹-norm
3-element Vector{Float64}:
  0.5
 -1.0
  1.5
```
