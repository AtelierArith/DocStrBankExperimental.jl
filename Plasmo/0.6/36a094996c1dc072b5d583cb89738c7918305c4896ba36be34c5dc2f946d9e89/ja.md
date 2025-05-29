```
identify_edges(hyper::HyperGraphProjection, node_vectors::Vector{Vector{OptiNode}})
```

オプティノードパーティションのベクトルから誘導されたエッジとエッジセパレーターを特定します。

# 引数

  * `hyper::HyperGraphProjection`: `hyper_projection`から得られた`HyperGraphProjection`。
  * `node_vectors::Vector{Vector{OptiNode}}`: `OptiNode`を含むベクトルのベクトル。

# 戻り値

  * partition_optiedges::Vector{Vector{OptiEdge}}: 各パーティションのための`OptiEdge`ベクトル。
  * cross_optiedges::Vector{OptiEdge}: パーティションを横切るオプティエッジのベクトル。
