```
SmallVector{N,T} <: AbstractSmallVector{N,T}

SmallVector{N,T}()
SmallVector{N,T}(iter)
SmallVector{N}(iter)
SmallVector(v::PackedVector{T})
SmallVector(v::AbstractSmallVector)
```

`SmallVector{N,T}` は、型 `T` の要素を最大 `N` 個保持できる不変ベクトル型です。ここで `N` は任意の（小さな）正の整数です。ただし、ビット整数およびハードウェア浮動小数点型の場合、通常 `N` は `2` の累乗とされます。

要素型 `T` は、要素型を持つイテレータから `SmallVector` を作成する際に省略可能です。たとえば、`AbstractVector` やタプルから作成する場合です。この場合、`T` はタプルの要素型を昇格させることによって決定されます。引数が与えられない場合、空のベクトルが返されます。`AbstractSmallVector` または `PackedVector` `v` から `SmallVector` が作成され、パラメータ `N` が省略された場合、`N` は `v` の容量に設定されます。

`SmallVector{N,T}` の未使用要素は、`default(T)` の値で埋められます。これは、`Number` を含むいくつかの型に対して事前定義されています。他の型のデフォルト値は明示的に定義する必要があります。

2つの `SmallVector` の加算および減算は、ベクトルの容量が異なっていても可能です。（もちろん、長さは一致する必要があります。）この場合、結果の容量は引数の容量の小さい方になります。

他に [`MutableSmallVector`](@ref)、[`capacity`](@ref)、[`SmallCollections.default`](@ref)、`Base.IteratorEltype`、`promote_type` も参照してください。

# 例

```jldoctest
julia> v = SmallVector{8,Int8}(2*x for x in 1:3)
3-element SmallVector{8, Int8}:
 2
 4
 6

julia> w = SmallVector{9}((1, 2.5, 4))
3-element SmallVector{9, Float64}:
 1.0
 2.5
 4.0

julia> v+w
3-element SmallVector{8, Float64}:
  3.0
  6.5
 10.0
```
