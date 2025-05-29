```
gather(snd;destination=MAIN)
```

配列 `snd` の要素のコピーをベクトルに集めた最初のエントリを含む配列を返します。結果を格納するために、最初のものとは異なるコンポーネントを使用するには、オプションのキーワード引数 `destination` を設定します。 `destination=:all` を設定すると、結果は `rcv` のすべてのエントリに格納され、「すべてを集める」操作になります。

# 例

```jldoctest
julia> using PartitionedArrays

julia> snd = collect(1:3)
3-element Vector{Int64}:
 1
 2
 3

julia> gather(snd,destination=3)
3-element Vector{Vector{Int64}}:
 []
 []
 [1, 2, 3]

julia> gather(snd,destination=:all)
3-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [1, 2, 3]
 [1, 2, 3]
```
