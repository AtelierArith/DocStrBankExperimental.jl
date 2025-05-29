```
p8est_connectivity_complete(conn)
```

内部的に、tree*to*vertex情報に基づいて接続を行います。頂点のリストに固有でない周期性は失われます。

### パラメータ

  * `conn`:[in,out] 接続には適切な頂点とtree*to*vertexフィールドが必要です。tree*to*treeおよびtree*to*faceフィールドは割り当てられ、[`p8est_connectivity_is_valid`](@ref) (conn)を満たす必要がありますが、上書きされます。エッジおよびコーナーフィールドは解放され、新たに割り当てられます。

### プロトタイプ

```c
void p8est_connectivity_complete (p8est_connectivity_t * conn);
```
