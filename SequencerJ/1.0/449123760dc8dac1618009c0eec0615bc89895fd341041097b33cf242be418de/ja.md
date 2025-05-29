```
SequencerResult
    EOSeg::Dict{Tuple,Any} # セグメントごとの伸長と順序（BFS,DFS）のリスト    
    EOAlgScale::Dict{Tuple,Any} # 累積重み付き距離のための伸長と順序
    D::AbstractMatrix # 最終距離行列
    mst::LightGraphs.AbstractGraph # 最終最小全域木
    η::Real # 最終伸長
    order::AbstractVector # bfsからの最終順序
```

Type containing the results of a Sequencer run.
