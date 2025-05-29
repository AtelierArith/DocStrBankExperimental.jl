```
p4est_connectivity_reduce(conn)
```

接続性のコーナー情報を削除し、[`p4est_connectivity_complete`](@ref) を正常に実行するのに十分な情報が残るようにします。削減された接続性は、[`p4est_connectivity_is_valid`](@ref) を通過します。

### パラメータ

  * `conn`:[in,out] 削減される接続性。

### プロトタイプ

```c
void p4est_connectivity_reduce (p4est_connectivity_t * conn);
```
