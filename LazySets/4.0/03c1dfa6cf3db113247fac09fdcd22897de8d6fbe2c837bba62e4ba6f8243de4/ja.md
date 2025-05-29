# 拡張ヘルプ

```
isoperation(X::LazySet)
```

### アルゴリズム

デフォルトの実装は、入力のセットタイプが操作タイプであるかどうかを [`isoperationtype(::Type{<:LazySet})`](@ref) を使用してチェックします。

### 例

```jldoctest
julia> B = BallInf([0.0, 0.0], 1.0);

julia> isoperation(B)
false

julia> isoperation(B ⊕ B)
true
```
