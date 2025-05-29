```
t8_cmesh_uniform_bounds(cmesh, level, ts, first_local_tree, child_in_tree_begin, last_local_tree, child_in_tree_end, first_tree_shared)
```

現在のランクのための均一な森林のセクションを計算します。

# 引数

  * `cmesh`:[in] 考慮すべきcmesh。
  * `level`:[in] 作成する均一な細分化レベル。
  * `ts`:[in] 境界を計算するための要素スキーム。
  * `first_local_tree`:[out] 呼び出しプロセッサに属する要素を含む最初のツリー。
  * `child_in_tree_begin`:[out] 呼び出しプロセッサに属する最初の要素のグローバルインデックス。NULLの場合は計算されません。
  * `last_local_tree`:[out] 呼び出しプロセッサに属する要素を含む最後のツリー。
  * `child_in_tree_end`:[out] もはや呼び出しプロセッサに属さない最初の要素のグローバルインデックス。NULLの場合は計算されません。
  * `first_tree_shared`:[out] NULLでない場合、次のプロセスで*first*local*tree*が*last*local*tree*と同じかどうかに応じて1または0がここに格納されます。*cmesh*はこの関数を呼び出す前にコミットされている必要があります。*

### プロトタイプ

```c
void t8_cmesh_uniform_bounds (t8_cmesh_t cmesh, int level, const t8_scheme_cxx_t *ts, t8_gloidx_t *first_local_tree, t8_gloidx_t *child_in_tree_begin, t8_gloidx_t *last_local_tree, t8_gloidx_t *child_in_tree_end, int8_t *first_tree_shared);
```
