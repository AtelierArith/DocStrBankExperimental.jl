```
s_t_connectivity(source::Vector{Int}, target::Vector{Int})
```

指定された *source* ノードから *target* ノードへのパスが *system* 内で *components* のみが稼働状態で存在する場合に真を返す関数 (system::Matrix{Float64}, components::BitVector) を返します。
