```
CayleyMengerDistanceMatrix{T,Sz}(simplex_dimensions::Int, square_distances::Vector{T}) where {T<:Real,Sz::Union{Int,Dynamic}}
CayleyMengerDistanceMatrix(points::Vararg{NTuple{N,T},N+1})::CayleyMengerDistanceMatrix{T,N} where {T<:Real,N::Int}
CayleyMengerDistanceMatrix(P::AbstractMatrix{T})::CayleyMengerDistanceMatrix{T,Dynamic} where {T<:Real}
```

N-単体の点の間の平方距離のゼロ対角対称行列で、効率的な線形ストレージに基づいています。

`points`を提供する場合、Nの値を持つN+1のタプルでなければならず、これがN-単体の点の座標です。`P`を提供する場合、N+1行とN列を持つ縦長のほぼ正方行列でなければならず、行はN-単体の点の座標です。`simplex_dimensions`と`square_distances`を直接提供する場合、`simplex_dimensions`はN-単体の次元の整数値でなければならず、`square*distances`はN-単体の点の間の平方距離の事前計算されたバックアップ線形ストレージでなければならず、長さは`binomial2(simplex*dimensions + 1)`でなければなりません。
