```julia
connectivity(
    conn::FiniteElementContainers.VectorizedElementField{T, 2, NN, NE, Vals},
    e::Int64
) -> Union{SubArray{_A, 1, P, I, false} where {_A, P<:(FiniteElementContainers.VectorizedElementField{T, 2, NN, NE, Vals} where {T, NN, NE, Vals}), I<:Tuple{Base.Slice{T} where T<:Base.OneTo, Int64}}, SubArray{_A, 1, P, I, true} where {_A, P<:(FiniteElementContainers.VectorizedElementField{T, 2, NN, NE, Vals} where {T, NN, NE, Vals}), I<:Tuple{Base.Slice{T} where T<:Base.OneTo, Int64}}}

```
