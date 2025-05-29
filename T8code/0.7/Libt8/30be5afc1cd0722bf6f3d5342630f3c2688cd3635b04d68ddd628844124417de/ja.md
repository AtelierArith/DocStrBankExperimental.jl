```
t8_cmesh_get_num_ghosts(cmesh)
```

cmeshのゴーストツリーの数を返します。cmeshがパーティションされていない場合、これはt8*cmesh*get*num*treesに相当します。

# 引数

  * `cmesh`:[in] 考慮されるcmesh。

# 戻り値

cmeshのゴーストツリーの数。*cmesh*はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
t8_locidx_t t8_cmesh_get_num_ghosts (t8_cmesh_t cmesh);
```
