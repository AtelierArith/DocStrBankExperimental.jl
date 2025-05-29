```
SelectTransform(dims)
```

入力の次元 `dims` を選択する変換。

# 例

```jldoctest
julia> dims = [1, 3, 5, 6, 7]; t = SelectTransform(dims); X = rand(100, 10);

julia> map(t, ColVecs(X)) == ColVecs(X[dims, :])
true
```
