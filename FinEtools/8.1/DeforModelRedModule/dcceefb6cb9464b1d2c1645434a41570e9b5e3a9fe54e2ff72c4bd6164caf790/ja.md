```
stresscomponentmap(::Type{DeforModelRed1D})
```

応力成分シンボルからインデックスへのマッピングを構築する辞書。

# 例

応力ベクトルのどの成分が例えば sigma_x ですか？次のようにします。

```
julia> comp = stresscomponentmap(DeforModelRed1D)
Dict{Symbol,Int64} with 2 entries:
  :xx => 1
  :x  => 1

julia>

julia> comp[:x]
1
```
