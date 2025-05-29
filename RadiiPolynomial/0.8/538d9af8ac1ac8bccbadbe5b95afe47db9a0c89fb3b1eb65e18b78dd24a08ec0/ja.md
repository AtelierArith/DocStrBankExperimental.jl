```
Taylor <: BaseSpace
```

指定された次数のテイラー列の要素を持つテイラー列空間。

フィールド:

  * `order :: Int`

コンストラクタ:

  * `Taylor(::Int)`

参照: [`Fourier`](@ref) と [`Chebyshev`](@ref)。

# 例

```jldoctest
julia> s = Taylor(2)
Taylor(2)

julia> order(s)
2
```
