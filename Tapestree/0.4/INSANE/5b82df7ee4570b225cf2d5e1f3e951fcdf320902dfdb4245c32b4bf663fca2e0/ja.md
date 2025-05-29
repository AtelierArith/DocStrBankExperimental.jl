```
subclade(trees::Vector{T}, 
              ltree::sT_label, 
              tips ::Vector{String},
              stem ::Bool) where {T <: iTree}
```

`tips`に含まれるティップラベルを含む最小のサブクレードを返します。
