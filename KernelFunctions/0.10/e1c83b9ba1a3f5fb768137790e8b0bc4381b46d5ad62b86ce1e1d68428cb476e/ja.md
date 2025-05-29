```
ARDTransform(v::AbstractVector)
```

入力を要素ごとに `v` で乗算する変換です。

# 例

```jldoctest
julia> v = rand(10); t = ARDTransform(v); X = rand(10, 100);

julia> map(t, ColVecs(X)) == ColVecs(v .* X)
true
```
