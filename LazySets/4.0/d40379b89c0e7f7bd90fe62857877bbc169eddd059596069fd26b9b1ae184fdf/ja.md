```
project(cp::CartesianProduct{N,<:Interval,<:Union{VPolygon,VPolytope}
        block::AbstractVector{Int};
        [kwargs...]) where {N}
```

区間と頂点表現の集合の直積の具体的な射影。

### 入力

  * `cp`    – 区間と `VPolygon` または `VPolytope` の直積
  * `block` – ブロック構造、関心のある次元を持つベクトル

### 出力

`block` で指定された次元における直積 `cp` の射影を表す `VPolytope`。
