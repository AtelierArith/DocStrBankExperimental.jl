```
p4est_coarsen(p4est_, coarsen_recursive, coarsen_fn, init_fn)
```

フォレストを粗くします。

### パラメータ

  * `p4est`:[in,out] フォレストはその場で変更されます。
  * `coarsen_recursive`:[in] 再帰的な粗化を決定するためのブール値。
  * `coarsen_fn`:[in] 一群の四分木を粗くする必要がある場合にtrueを返すコールバック関数。
  * `init_fn`:[in] 自動的に既に割り当てられたuser_dataを初期化するためのコールバック関数。

### プロトタイプ

```c
void p4est_coarsen (p4est_t * p4est, int coarsen_recursive, p4est_coarsen_t coarsen_fn, p4est_init_t init_fn);
```
