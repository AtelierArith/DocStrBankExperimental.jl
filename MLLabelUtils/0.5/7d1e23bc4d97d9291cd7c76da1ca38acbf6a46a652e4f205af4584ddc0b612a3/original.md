```
labelmap2vec(dict) -> Vector
```

Inverse function of labelmap. Computes an `array` of labels by element-wise traversal of the entries in `dict`.

```
julia> labelvec = [:yes,:no,:no,:yes,:yes]

julia> lm = labelmap(labelvec)
Dict{Symbol,Array{Int64,1}} with 2 entries:
    :yes => [1, 4, 5]
    :no  => [2, 3]

julia> labelmap2vec(lm)
5-element Array{Symbol,1}:
    :yes
    :no
    :no
    :yes
    :yes
```
