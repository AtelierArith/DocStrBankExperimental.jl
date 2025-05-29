```
subclade(trees::Vector{T}, 
              ltree::sT_label, 
              tips ::Vector{String},
              stem ::Bool) where {T <: iTree}
```

Return the minimum subclade that includes tip labels in `tips`.
