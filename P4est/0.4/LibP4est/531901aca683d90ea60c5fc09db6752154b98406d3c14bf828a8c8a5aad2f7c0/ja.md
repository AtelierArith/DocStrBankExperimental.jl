```
p8est_mesh_quadrant_cumulative(p8est_, mesh, cumulative_id, which_tree, quadrant_id)
```

ローカルフォレスト内の累積番号に基づいて四分木を見つけます。メッシュ構造体の quad*to*tree フィールドが存在する場合、これは O(1) です。そうでない場合、プロセッサローカルツリーに対して二分探索を行います。

### パラメータ

  * `p8est`:[in] 作業するフォレスト。
  * `mesh`:[in] フォレストから派生したメッシュ。
  * `cumulative_id`:[in] 四分木のすべてのツリーに対する累積インデックス。ローカル（ゴーストでない）四分木を参照する必要があります。
  * `which_tree`:[in,out] NULL でない場合、入力値は -1 または四分木の初期推測であり、出力は返された四分木のツリーです。
  * `quadrant_id`:[out] NULL でない場合、ツリー内の四分木の番号。

### 戻り値

特定された四分木。

### プロトタイプ

```c
p8est_quadrant_t *p8est_mesh_quadrant_cumulative (p8est_t * p8est, p8est_mesh_t * mesh, p4est_locidx_t cumulative_id, p4est_topidx_t * which_tree, p4est_locidx_t * quadrant_id);
```
