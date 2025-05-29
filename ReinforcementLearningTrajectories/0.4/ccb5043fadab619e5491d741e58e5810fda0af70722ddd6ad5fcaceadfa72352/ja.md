```
SumTree(capacity::Int)
```

効率的に重みをサンプリングおよび更新します。詳細については、[こちら](https://jaromiru.com/2016/11/07/lets-make-a-dqn-double-learning-and-prioritized-experience-replay/)の投稿を参照してください。ここでは、ベクトルを使用して二分木を表現します。最大で `capacity` の葉を持つと仮定します。新しいノードを木に `push!` するたびに、最近の `capacity` ノードとその合計のみが更新されます！ [––––––親ノード––––––][––––葉––––] [サイズ: 2^ceil(Int, log2(capacity))-1 ][     サイズ: capacity   ]

# 例

```julia
julia> t = SumTree(8)
0-element SumTree
julia> for i in 1:16
       push!(t, i)
       end
julia> t
8-element SumTree:
  9.0
 10.0
 11.0
 12.0
 13.0
 14.0
 15.0
 16.0
julia> rand(t)
(2, 10.0)
julia> rand(t)
(1, 9.0)
julia> inds, ps = rand(t,100000)
([8, 4, 8, 1, 5, 2, 2, 7, 6, 6  …  1, 1, 7, 1, 6, 1, 5, 7, 2, 7], [16.0, 12.0, 16.0, 9.0, 13.0, 10.0, 10.0, 15.0, 14.0, 14.0  …  9.0, 9.0, 15.0, 9.0, 14.0, 9.0, 13.0, 15.0, 10.0, 15.0])
julia> countmap(inds)
Dict{Int64,Int64} with 8 entries:
  7 => 14991
  4 => 12019
  2 => 10003
  3 => 11027
  5 => 12971
  8 => 16052
  6 => 13952
  1 => 8985
julia> countmap(ps)
Dict{Float64,Int64} with 8 entries:
  9.0  => 8985
  13.0 => 12971
  10.0 => 10003
  14.0 => 13952
  16.0 => 16052
  11.0 => 11027
  15.0 => 14991
  12.0 => 12019
```
