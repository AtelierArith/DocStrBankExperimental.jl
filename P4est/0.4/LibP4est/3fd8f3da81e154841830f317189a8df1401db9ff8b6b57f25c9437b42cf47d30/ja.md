```
p4est_connectivity_complete(conn)
```

内部的に、tree*to*vertex 情報に基づいて接続を行います。頂点のリストに固有でない周期性は失われます。

### パラメータ

  * `conn`:[in,out] 接続には適切な頂点と tree*to*vertex フィールドが必要です。tree*to*tree および tree*to*face フィールドは割り当てられ、[`p4est_connectivity_is_valid`](@ref) (conn) を満たす必要がありますが、上書きされます。コーナーフィールドは解放され、新たに割り当てられます。

### プロトタイプ

```c
void p4est_connectivity_complete (p4est_connectivity_t * conn);
```
