```
groupunique(groups, values)
```

対応する `groups` の要素によって `values` のユニークな要素を集め、セットの辞書を返します。

# 例

```julia
julia> groupunique([true,false,true,false,true], [1,2,1,2,3])
2-element Dictionary{Bool,Indices{Int64}}
  true │ {1, 3}
 false │ {2}
```
