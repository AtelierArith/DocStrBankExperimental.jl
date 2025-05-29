```
t8_cmesh_treeid_is_ghost(cmesh, ltreeid)
```

与えられた [`t8_locidx_t`](@ref) が cmesh のゴーストに属するかどうかを照会します。

# 引数

  * `cmesh`:[in] 考慮すべき cmesh。
  * `ltreeid`:[in] （可能な）ゴーストインデックス。

# 戻り値

*ltreeid* が *cmesh* のゴーストツリーの範囲と一致する場合は真、そうでない場合は偽を返します。*cmesh* はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
int t8_cmesh_treeid_is_ghost (const t8_cmesh_t cmesh, const t8_locidx_t ltreeid);
```
