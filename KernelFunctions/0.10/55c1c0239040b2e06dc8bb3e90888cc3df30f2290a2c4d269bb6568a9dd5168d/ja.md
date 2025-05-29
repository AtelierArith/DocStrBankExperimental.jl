```
ScaleTransform(l::Real)
```

入力を要素ごとに `l` で乗算する変換です。

# 例

```jldoctest
julia> l = rand(); t = ScaleTransform(l); X = rand(100, 10);

julia> map(t, ColVecs(X)) == ColVecs(l .* X)
true
```
