```
t8_cmesh_ltreeid_to_ghostid(cmesh, ltreeid)
```

与えられたローカルツリーIDがゴーストに属する場合、そのゴーストのインデックスを返します。

# 引数

  * `cmesh`:[in] 考慮すべきcmesh。
  * `ltreeid`:[in] ゴーストのローカルIDで、t8*cmesh*treeid*is*ghostを満たし、したがって num*trees <= *ltreeid* < num*trees + num_ghosts

# 戻り値

すべてのゴースト内のゴーストのインデックス、したがってインデックス 0 <= index < num_ghosts *cmesh* はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
t8_locidx_t t8_cmesh_ltreeid_to_ghostid (const t8_cmesh_t cmesh, const t8_locidx_t ltreeid);
```
