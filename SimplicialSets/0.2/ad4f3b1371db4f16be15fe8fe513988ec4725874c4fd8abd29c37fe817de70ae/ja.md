```
AddToMul{T}
```

型 `T` に対して定義された加法群構造を乗法構造に変換するラッパーです。

# 例

```jldoctest
julia> x, y = AddToMul(2), AddToMul(3)
(2, 3)

julia> x*y
5

julia> x^2
4

julia> inv(x)
-2

julia> x/y
-1

julia> one(x)
0
```
