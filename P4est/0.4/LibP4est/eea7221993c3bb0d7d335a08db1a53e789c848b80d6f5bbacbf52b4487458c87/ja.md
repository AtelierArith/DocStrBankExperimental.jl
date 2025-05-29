```
p8est_mesh_memory_used(mesh)
```

メッシュ構造体のメモリ使用量を計算します。

### パラメータ

  * `mesh`:[in] メッシュ構造体。

### 戻り値

バイト単位の使用メモリ。

### プロトタイプ

```c
size_t p8est_mesh_memory_used (p8est_mesh_t * mesh);
```
