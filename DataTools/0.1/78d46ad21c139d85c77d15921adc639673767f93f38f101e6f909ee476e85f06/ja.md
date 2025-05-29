```
modifying(; $property₁ = f₁, ..., $propertyₙ = fₙ) -> g::Function
modifying(lens₁ => f₁, ..., lensₙ => fₙ) -> g::Function
```

関数 `fᵢ` を `propertyᵢ` または `lensᵢ` で指定された場所で実行する関数を作成します。

キーワード専用メソッド `modifying(; a = f₁, b = f₂)` は `modifying(@len(_.a) => f₁, @len(_.b) => f₂)` と同等です。

単項メソッド `g(x)` は次のように等価です。

```julia
x = modify(f₁, x, lens₁)
x = modify(f₂, x, lens₂)
...
x = modify(fₙ, x, lensₙ)
```

二項メソッド `g(x, y)` は次のように等価です。

```julia
x = set(x, lens₁, f₁(lens₁(x)), lens₁(y))
x = set(x, lens₂, f₂(lens₂(x)), lens₂(y))
...
x = set(x, lensₙ, fₙ(lensₙ(x)), lensₙ(y))
```

指定されていないレンズによって指定された場所は、`x` の値を保持します。これは `mergewith` の動作に似ています。

# 例

```jldoctest
julia> using DataTools

julia> map(modifying(a = string), [(a = 1, b = 2), (a = 3, b = 4)])
2-element Array{NamedTuple{(:a, :b),Tuple{String,Int64}},1}:
 (a = "1", b = 2)
 (a = "3", b = 4)

julia> reduce(modifying(a = +), [(a = 1, b = 2), (a = 3, b = 4)])
(a = 4, b = 2)

julia> using Accessors

julia> map(modifying(@optic(_.a[1].b) => x -> 10x),
           [(a = ((b = 1,), 2),), (a = ((b = 3,), 4),)])
2-element Array{NamedTuple{(:a,),Tuple{Tuple{NamedTuple{(:b,),Tuple{Int64}},Int64}}},1}:
 (a = ((b = 10,), 2),)
 (a = ((b = 30,), 4),)
```
