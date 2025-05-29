```
(order,can_be_deallocated,max_nodes)=get_topo_order(
    graph;
    priohelp = Dict{Symbol,Float64}(),
    free_mem_bonus = 1000,
    will_not_dealloc = [:I],
    input = :A,
)
```

`graph`のトポロジカルソートを計算します。つまり、グラフが表す関数を評価できるようにノードの順序を決定します。`priohelp`キーワード引数を使用すると、ノードの優先度を変更することで異なるトポロジカル順序を取得できます。このコードは、ノード`:I`と`input`は計算する必要がないと仮定しています。

このコードは、パス幅を最小化するためのヒューリスティックを使用しています。これはポイントシステムに基づいています。`priohelp`を提供することで計算順序に影響を与えることができます。ノード`:B4`を早く計算したい場合は、`priohelp[:B4]=-5000.0`を設定できます。`free_mem_bonus`は、他のノードを解放するノードの計算を優先するためにヒューリスティックで使用されます。ベクター`will_not_deallocate`は、解放されないノードを指定することで順序に影響を与え、そのため`free_mem_bonus`は得られません。

返り値`order`は`Symbol`の`Vector`であり、`can_be_deallocated`は`Vector{Vector{Symbol}}`で、要素`i`は順序のステップ`i`の後に未使用の`Symbols`を指定します。`max_nodes`はパス幅です。
