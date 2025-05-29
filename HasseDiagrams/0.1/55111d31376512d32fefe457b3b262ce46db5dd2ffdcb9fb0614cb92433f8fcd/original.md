```
set_labels!(h::HasseDiagram, labs::Dict{Int,T}) where {T}
```

Label element `j` with `labs[j]` when drawing the poset. 

If `labs` is omitted, reset the labels to the default in which  element `j` is labeled `j`.
