```
algorithm2_2!(p::Vector{T}, Is::NTuple{M, Vector{Int}}, ws::NTuple{M, Vector{<:Real}}) where {T<:Real, M}
```

Fill `p` with the probabilities that result from normalizing the element-wise product of weights selected by the index set, `Is[m]`, respective to each weight vector, `ws[m]`. Note that `T` must be a type which is able to hold the result of `inv(one(T))`.

See also: [`algorithm2_2`](@ref)

# Examples

```jldoctest
julia> Is = ([1,2,3], [4,5,6], [7,8,9]); ws = ([1,2,3], fill(1/6, 6), fill(1//10, 9));

julia> algorithm2_2!(zeros(3), Is, ws)
3-element Vector{Float64}:
 0.16666666666666666
 0.3333333333333333
 0.5

julia> algorithm2_2!(zeros(Rational{Int}, 3), Is, (ws[1], fill(1//6, 6), ws[3]))
3-element Vector{Rational{Int64}}:
 1//6
 1//3
 1//2
```
