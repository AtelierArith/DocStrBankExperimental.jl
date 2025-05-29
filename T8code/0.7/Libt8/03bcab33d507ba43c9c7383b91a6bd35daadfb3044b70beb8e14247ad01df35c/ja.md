```
t8_cmesh_tree_face_is_boundary(cmesh, ltree_id, face)
```

ローカルツリーまたはゴーストの面がドメイン境界にあるかどうかを照会します。

# 引数

  * `cmesh`:[in] 考慮すべきcmesh。
  * `ltree_id`:[in] ツリーのローカルID。
  * `face`:[in] ツリーの面の番号。

# 戻り値

面がドメイン境界にある場合はTrue。そうでない場合はFalse。*cmesh*はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
int t8_cmesh_tree_face_is_boundary (t8_cmesh_t cmesh, t8_locidx_t ltree_id, int face);
```
