```
group(groups, values)
```

`values`の要素を、`groups`の対応する要素によって示されるラベルでグループ化した辞書を返します。

# 例

```julia
julia> group([true,false,true,false,true], [1,2,3,4,5])
2-element Dictionary{Bool,Array{Int64,1}}
  true │ [1, 3, 5]
 false │ [2, 4]
```
