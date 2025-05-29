```
p8est_coarsen_ext(p8est_, coarsen_recursive, callback_orphans, coarsen_fn, init_fn, replace_fn)
```

フォレストを粗くします。

### パラメータ

  * `p8est`:[in,out] フォレストはその場で変更されます。
  * `coarsen_recursive`:[in] 再帰的な粗化を決定するためのブール値。
  * `callback_orphans`:[in] 非ファミリーに対しても coarsen*fn を呼び出すことを有効にするためのブール値。この場合、コールバックの引数リスト内の第二象限ポインタは NULL であり、以降のポインタは未定義であり、戻り値は無視されます。coarsen*recursive が true の場合、象限が孤児として一度以上呼び出され、最終的にファミリーの一部になる可能性があります。coarsen*recursive が false で callback*orphans が true の場合、すべての象限が coarsen_fn コールバックに正確に一度だけ渡されることが保証されます。
  * `coarsen_fn`:[in] 象限のファミリーを粗くする必要がある場合に true を返すコールバック関数。
  * `init_fn`:[in] 自動的に既に割り当てられた user_data を初期化するためのコールバック関数。
  * `replace_fn`:[in] ユーザーが置き換える象限に基づいて受信する象限を変更できるようにするコールバック関数。

### プロトタイプ

```c
void p8est_coarsen_ext (p8est_t * p8est, int coarsen_recursive, int callback_orphans, p8est_coarsen_t coarsen_fn, p8est_init_t init_fn, p8est_replace_t replace_fn);
```
