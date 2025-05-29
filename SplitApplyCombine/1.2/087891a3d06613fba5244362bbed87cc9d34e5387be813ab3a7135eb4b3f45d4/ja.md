```
groupfind([by], container)
```

`container`のインデックス`i`を`by(container[i])`でラベル付けされたグループに分けます。`by`のデフォルト値は`identity`です。

# 例

```jldoctest
julia> groupfind(iseven, [3,4,2,6,5,8])
2-element Dictionary{Bool,Array{Int64,1}}
 false │ [1, 5]
  true │ [2, 3, 4, 6]
```
