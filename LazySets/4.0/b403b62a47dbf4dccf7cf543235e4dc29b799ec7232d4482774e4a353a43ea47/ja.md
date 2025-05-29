# 拡張ヘルプ

```
isequivalent(X::LazySet, Y::LazySet)
```

### アルゴリズム

デフォルトの実装はまず `X ≈ Y` をチェックします。これは `X` と `Y` が同じ基本型を持ち、ほぼ同じ値を持つ場合にのみ `true` を返します。それが失敗した場合、実装は二重包含 `X ⊆ Y && Y ⊆ X` をチェックします。

### 例

```jldoctest
julia> X = BallInf([0.1, 0.2], 0.3);

julia> Y = convert(HPolytope, X);

julia> X == Y
false

julia> isequivalent(X, Y)
true
```
