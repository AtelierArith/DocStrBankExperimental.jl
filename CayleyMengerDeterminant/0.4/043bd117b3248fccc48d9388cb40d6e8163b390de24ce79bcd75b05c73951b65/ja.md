```
simplex_volume(distances::CayleyMengerDistanceMatrix{T,Sz}; distance_type::Union{Nothing,Type{<:Real}} = nothing) where {N,T<:Real}
simplex_volume(points::Vararg{NTuple{N,T},N+1}; distance_type::Union{Nothing,Type{<:Real}} = nothing) where {N,T<:Real}
simplex_volume(P::AbstractMatrix{T}; distance_type::Union{Nothing,Type{<:Real}} = nothing) where {T<:Real}
```

与えられた点の座標を使用して、Cayley-Menger行列式を用いて`N`-単体の（内部）測度を計算します。これは、点間の平方距離を含みます。

例えば、`N == 2`の場合、この関数は3つの点の2次元座標を与えられたときに三角形の面積を計算します。同様に、`N == 3`の場合、この関数は4つの点の3次元座標を与えられたときに四面体の体積を計算します。

`points`を提供する場合、N+1のタプルで各タプルはNの値を持ち、これが`N`-単体の点の座標です。`P`を提供する場合、N+1行とN列を持つ縦長の近似正方行列でなければなりません。行は`N`-単体の点の座標です。

`distance_type`が提供され、`nothing`でない場合、平方距離に関する内部計算は`distance_type`を型として使用して行われます。そうでない場合、内部計算に使用される型は自動的に`T`から導出されます。
