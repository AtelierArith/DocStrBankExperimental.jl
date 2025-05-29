```
t8_cmesh_treeid_is_local_tree(cmesh, ltreeid)
```

与えられた [`t8_locidx_t`](@ref) が cmesh のローカルツリーに属するかどうかを照会します。

# 引数

  * `cmesh`:[in] 考慮すべき cmesh。
  * `ltreeid`:[in] （可能な）ツリーインデックス。

# 戻り値

*ltreeid* が *cmesh* のローカルツリーの範囲と一致する場合は真、そうでない場合は偽を返します。*cmesh* はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
int t8_cmesh_treeid_is_local_tree (const t8_cmesh_t cmesh, const t8_locidx_t ltreeid);
```
