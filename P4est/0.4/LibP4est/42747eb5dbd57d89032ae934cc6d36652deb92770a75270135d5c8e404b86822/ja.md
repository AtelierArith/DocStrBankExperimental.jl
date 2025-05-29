```
p8est_find_quadrant_cumulative(p8est_, cumulative_id, which_tree, quadrant_id)
```

フォレスト内の累積番号によってローカルクアドラントを検索します。

プロセッサローカルツリーに対して二分探索を行うため、可能であればこの関数を使用しないことが推奨され、呼び出しコード内でO(1)のツリーコンテキスト情報を維持するように努めるべきです。

### パラメータ

  * `p8est`:[in] 作業するフォレスト。
  * `cumulative_id`:[in] クアドラントのすべてのツリーに対する累積インデックス。
  * `which_tree`:[in,out] NULLでない場合、入力値は-1またはクアドラントのツリーに対する初期推測であることができます。初期推測は、空でないローカルツリーのインデックスでなければなりません。出力は返されたクアドラントのツリーです。
  * `quadrant_id`:[out] NULLでない場合、ツリー内のクアドラントの番号。

### 戻り値

特定されたクアドラント。

### プロトタイプ

```c
p8est_quadrant_t *p8est_find_quadrant_cumulative (p8est_t * p8est, p4est_locidx_t cumulative_id, p4est_topidx_t * which_tree, p4est_locidx_t * quadrant_id);
```
