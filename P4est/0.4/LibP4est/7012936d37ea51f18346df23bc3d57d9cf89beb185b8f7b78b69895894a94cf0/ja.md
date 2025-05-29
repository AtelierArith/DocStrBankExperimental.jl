```
p4est_coarsen_ext(p4est_, coarsen_recursive, callback_orphans, coarsen_fn, init_fn, replace_fn)
```

森林を粗くします。

### パラメータ

  * `p4est`:[in,out] 森はその場で変更されます。
  * `coarsen_recursive`:[in] 再帰的な粗化を決定するためのブール値。
  * `callback_orphans`:[in] 非ファミリーに対してもcoarsen*fnを呼び出すことを有効にするためのブール値。この場合、コールバックの引数リストの第2象限ポインタはNULLであり、以降のポインタは未定義であり、戻り値は無視されます。coarsen*recursiveがtrueの場合、象限が孤児として1回以上呼び出され、最終的にファミリーの一部になる可能性があります。coarsen*recursiveがfalseでcallback*orphansがtrueの場合、すべての象限がcoarsen_fnコールバックに正確に1回渡されることが保証されます。
  * `coarsen_fn`:[in] 象限のファミリーを粗くする必要がある場合にtrueを返すコールバック関数。
  * `init_fn`:[in] 自動的に既に割り当てられたuser_dataを初期化するためのコールバック関数。
  * `replace_fn`:[in] ユーザーが置き換える象限に基づいて受信する象限を変更できるようにするコールバック関数。

### プロトタイプ

```c
void p4est_coarsen_ext (p4est_t * p4est, int coarsen_recursive, int callback_orphans, p4est_coarsen_t coarsen_fn, p4est_init_t init_fn, p4est_replace_t replace_fn);
```
