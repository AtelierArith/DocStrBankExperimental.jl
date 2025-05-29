```
p6est_coarsen_columns_ext(p6est_, coarsen_recursive, callback_orphans, coarsen_fn, init_fn, replace_fn)
```

森林を水平方向に粗くします。

### パラメータ

  * `p6est`:[in,out] 森はその場で変更されます。
  * `coarsen_recursive`:[in] 再帰的な粗化を決定するためのブール値。
  * `callback_orphans`:[in] 非ファミリーに対してもcoarsen*fnを呼び出すことを可能にするブール値。この場合、コールバックの引数リストの第2象限ポインタはNULLであり、以降のポインタは未定義であり、戻り値は無視されます。coarsen*recursiveがtrueの場合、象限が孤児として1回以上呼び出され、最終的にファミリーの一部になる可能性があります。
  * `coarsen_fn`:[in] 象限のファミリーを粗くする必要がある場合にtrueを返すコールバック関数。
  * `init_fn`:[in] 自動的に既に割り当てられたuser_dataを初期化するためのコールバック関数。
  * `replace_fn`:[in] ユーザーが置き換える象限に基づいて受信する象限を変更できるようにするコールバック関数。

### プロトタイプ

```c
void p6est_coarsen_columns_ext (p6est_t * p6est, int coarsen_recursive, int callback_orphans, p6est_coarsen_column_t coarsen_fn, p6est_init_t init_fn, p6est_replace_t replace_fn);
```
