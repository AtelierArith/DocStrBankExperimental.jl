```
CartesianPower{T<:VectorSpace} <: CartesianSpace
```

同じ [`VectorSpace`](@ref) の直積から得られるカートesian空間。

フィールド:

  * `space :: T`
  * `n :: Int`

コンストラクタ:

  * `CartesianPower(::VectorSpace, ::Int)`
  * `^(::VectorSpace, ::Int)`: `CartesianPower(::VectorSpace, ::Int)` と同等

参照: [`^(::VectorSpace, ::Int)`](@ref), [`CartesianProduct`](@ref) および [`×`](@ref).

# 例

```jldoctest
julia> s = CartesianPower(Taylor(1), 3)
Taylor(1)³

julia> space(s)
Taylor(1)

julia> nspaces(s)
3
```
