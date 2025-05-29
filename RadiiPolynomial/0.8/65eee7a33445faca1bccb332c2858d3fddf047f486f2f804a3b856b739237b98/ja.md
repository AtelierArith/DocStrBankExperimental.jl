```
Chebyshev <: BaseSpace
```

指定された次数のチェビシェフ列の要素を持つチェビシェフ列空間。

フィールド:

  * `order :: Int`

コンストラクタ:

  * `Chebyshev(::Int)`

参照: [`Taylor`](@ref) および [`Fourier`](@ref)。

# 例

```jldoctest
julia> s = Chebyshev(2)
Chebyshev(2)

julia> order(s)
2
```
