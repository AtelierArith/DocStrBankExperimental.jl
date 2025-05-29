```
labelmap2vec(dict) -> Vector
```

labelmapの逆関数。`dict`のエントリを要素ごとに走査することによって、ラベルの`array`を計算します。

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
