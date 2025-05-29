```
p4est_mesh_quadrant_cumulative(p4est_, mesh, cumulative_id, which_tree, quadrant_id)
```

ローカルフォレスト内の累積番号に基づいて四分木を見つけます。メッシュ構造体のquad*to*treeフィールドが存在する場合、これはO(1)です。そうでない場合、プロセッサローカルツリーに対して二分探索を行います。

### パラメータ

  * `p4est`:[in] 作業するフォレスト。
  * `mesh`:[in] フォレストから派生したメッシュ。
  * `cumulative_id`:[in] 四分木のすべてのツリーに対する累積インデックス。ローカル（非ゴースト）四分木を参照する必要があります。
  * `which_tree`:[in,out] NULLでない場合、入力値は-1または四分木の初期推測であり、出力は返された四分木のツリーです。
  * `quadrant_id`:[out] NULLでない場合、ツリー内の四分木の番号。

### 戻り値

識別された四分木。

### プロトタイプ

```c
p4est_quadrant_t *p4est_mesh_quadrant_cumulative (p4est_t * p4est, p4est_mesh_t * mesh, p4est_locidx_t cumulative_id, p4est_topidx_t * which_tree, p4est_locidx_t * quadrant_id);
```
