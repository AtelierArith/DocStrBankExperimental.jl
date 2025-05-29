```
onehot(x, labels, [default])
```

Returns a [`OneHotVector`](@ref) which is roughly a sparse representation of `x .== labels`.

Instead of storing say `Vector{Bool}`, it stores the index of the first occurrence  of `x` in `labels`. If `x` is not found in labels, then it either returns `onehot(default, labels)`, or gives an error if no default is given.

See also [`onehotbatch`](@ref) to apply this to many `x`s,  and [`onecold`](@ref) to reverse either of these, as well as to generalise `argmax`.

# Examples

```jldoctest
julia> β = onehot(:b, (:a, :b, :c))
3-element OneHotVector(::UInt32) with eltype Bool:
 ⋅
 1
 ⋅

julia> αβγ = (onehot(0, 0:2), β, onehot(:z, [:a, :b, :c], :c))  # uses default
(Bool[1, 0, 0], Bool[0, 1, 0], Bool[0, 0, 1])

julia> hcat(αβγ...)  # preserves sparsity
3×3 OneHotMatrix(::Vector{UInt32}) with eltype Bool:
 1  ⋅  ⋅
 ⋅  1  ⋅
 ⋅  ⋅  1
```
