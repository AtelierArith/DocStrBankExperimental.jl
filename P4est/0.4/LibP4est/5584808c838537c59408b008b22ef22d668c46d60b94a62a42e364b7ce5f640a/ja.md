```
p4est_find_quadrant_cumulative(p4est_, cumulative_id, which_tree, quadrant_id)
```

森林内の累積番号によってローカル四分木を検索します。

プロセッサローカルツリーに対して二分探索を行うため、可能であればこの関数を使用しないことが推奨され、呼び出しコード内でO(1)のツリーコンテキスト情報を維持するように努めるべきです。

### パラメータ

  * `p4est`:[in] 作業する森林。
  * `cumulative_id`:[in] 四分木のすべてのツリーに対する累積インデックス。
  * `which_tree`:[in,out] NULLでない場合、入力値は-1または四分木のツリーに対する初期推測であることができます。初期推測は空でないローカルツリーのインデックスでなければなりません。出力は返された四分木のツリーです。
  * `quadrant_id`:[out] NULLでない場合、ツリー内の四分木の番号。

### 戻り値

特定された四分木。

### プロトタイプ

```c
p4est_quadrant_t *p4est_find_quadrant_cumulative (p4est_t * p4est, p4est_locidx_t cumulative_id, p4est_topidx_t * which_tree, p4est_locidx_t * quadrant_id);
```
