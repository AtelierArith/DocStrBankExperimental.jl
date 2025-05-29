```
multicast(snd;source=MAIN)
```

`snd[source]`を`snd`と同じサイズと型の新しい配列にコピーします。

# 例

```jldoctest
julia> using PartitionedArrays

julia> a = [0,0,2,0]
4-element Vector{Int64}:
 0
 0
 2
 0

julia> multicast(a,source=3)
4-element Vector{Int64}:
 2
 2
 2
 2
```
