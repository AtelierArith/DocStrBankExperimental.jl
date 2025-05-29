```
p8est_mesh_get_quadrant(p4est_, mesh, qid)
```

フォレスト内のプロセスローカルな四分木にアクセスします。quad*to*tree配列が populated されたメッシュが必要です。これは p8est*mesh*quadrant_cumulative の特別なケースです。

### パラメータ

  * `p4est`:[in] フォレスト。
  * `mesh`:[in] メッシュ。
  * `qid`:[in] 四分木のプロセスローカルID（木に対して累積）。

### 戻り値

要求された四分木へのポインタ。

### プロトタイプ

```c
p8est_quadrant_t *p8est_mesh_get_quadrant (p8est_t * p4est, p8est_mesh_t * mesh, p4est_locidx_t qid);
```
