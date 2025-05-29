```
SequencerResult
    EOSeg::Dict{Tuple,Any} # list of elongation and orderings (BFS,DFS), one per Segment    
    EOAlgScale::Dict{Tuple,Any} # elongation and orderings for the cumulated weighted distances
    D::AbstractMatrix # final distance matrix
    mst::LightGraphs.AbstractGraph # final mst
    η::Real # final elongation
    order::AbstractVector #final ordering from bfs
```

Type containing the results of a Sequencer run.
