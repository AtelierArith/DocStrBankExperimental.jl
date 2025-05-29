```
exchange(snd,graph::ExchangeGraph) -> Task
```

Send the data in `snd` according the directed graph `graph`. This function returns immediately and returns a task that produces the result, allowing for latency hiding. Use `fetch` to wait and get the result. The object `snd` and `rcv=fetch(exchange(snd,graph))` are array of vectors. The  value `snd[i][j]` is sent to node `graph.snd[i][j]`. The value `rcv[i][j]` is the one received from  node `graph.rcv[i][j]`.

# Examples

```jldoctest
julia> using PartitionedArrays

julia> snd_ids = [[3,4],[1,3],[1,4],[2]]
4-element Vector{Vector{Int64}}:
 [3, 4]
 [1, 3]
 [1, 4]
 [2]

julia> graph = ExchangeGraph(snd_ids)
ExchangeGraph{Vector{Vector{Int64}}} with 4 nodes


julia> snd = [[10,10],[20,20],[30,30],[40]]
4-element Vector{Vector{Int64}}:
 [10, 10]
 [20, 20]
 [30, 30]
 [40]

julia> t = exchange(snd,graph);

julia> rcv = fetch(t)
4-element Vector{Vector{Int64}}:
 [20, 30]
 [40]
 [10, 20]
 [10, 30]
```
