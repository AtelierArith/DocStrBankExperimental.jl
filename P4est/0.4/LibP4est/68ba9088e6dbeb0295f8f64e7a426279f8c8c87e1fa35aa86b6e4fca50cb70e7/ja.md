```
p6est_coarsen_layers(p6est_, coarsen_recursive, coarsen_fn, init_fn)
```

シートの層を粗くします。

### パラメータ

  * `p6est`:[in,out] 森はその場で変更されます。
  * `coarsen_recursive`:[in] 再帰的な粗化を決定するためのブール値。
  * `coarsen_fn`:[in] 層のファミリーを粗くする必要がある場合にtrueを返すコールバック関数。
  * `init_fn`:[in] 自動的に既に割り当てられたuser_dataを初期化するためのコールバック関数。

### プロトタイプ

```c
void p6est_coarsen_layers (p6est_t * p6est, int coarsen_recursive, p6est_coarsen_layer_t coarsen_fn, p6est_init_t init_fn);
```
