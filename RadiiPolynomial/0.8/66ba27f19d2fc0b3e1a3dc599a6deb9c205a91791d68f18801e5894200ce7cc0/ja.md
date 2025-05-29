```
Fourier{T<:Real} <: BaseSpace
```

指定された次数と周波数のフーリエ列の要素を持つフーリエ列空間。

フィールド:

  * `order :: Int`
  * `frequency :: T`

コンストラクタ:

  * `Fourier(::Int, ::Real)`

参照: [`Taylor`](@ref) と [`Chebyshev`](@ref)。

# 例

```jldoctest
julia> s = Fourier(2, 1.0)
Fourier(2, 1.0)

julia> order(s)
2

julia> frequency(s)
1.0
```
