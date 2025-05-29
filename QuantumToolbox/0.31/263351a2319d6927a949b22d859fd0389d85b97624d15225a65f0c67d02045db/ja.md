```
multisite_operator(dims::Union{AbstractVector, Tuple}, pairs::Pair{<:Integer,<:QuantumObject}...)
```

多サイト演算子を生成するためのJulia関数 $\\hat{O} = \\hat{O}_i \\hat{O}_j \\cdots \\hat{O}_k$。この関数は、次元のベクトル `dims` と、ペアのリスト `pairs` を受け取ります。ペアの最初の要素はサイトインデックスで、2番目の要素はそのサイトに作用する演算子です。

# 引数

  * `dims::Union{AbstractVector, Tuple}`: 格子の次元のベクトル。
  * `pairs::Pair{<:Integer,<:QuantumObject}...`: ペアのリストで、ペアの最初の要素はサイトインデックス、2番目の要素はそのサイトに作用する演算子です。

# 戻り値

`QuantumObject`: マルチサイト演算子を表す `QuantumObject`。

# 例

```jldoctest
julia> op = multisite_operator(Val(8), 5=>sigmax(), 7=>sigmaz());

julia> op.dims
8-element StaticArraysCore.SVector{8, Int64} with indices SOneTo(8):
 2
 2
 2
 2
 2
 2
 2
 2
```
