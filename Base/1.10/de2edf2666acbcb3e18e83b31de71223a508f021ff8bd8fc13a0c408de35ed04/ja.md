```
isabstracttype(T)
```

型 `T` が抽象型として宣言されたかどうかを判断します（すなわち、`abstract type` 構文を使用して）。

# 例

```jldoctest
julia> isabstracttype(AbstractArray)
true

julia> isabstracttype(Vector)
false
```
