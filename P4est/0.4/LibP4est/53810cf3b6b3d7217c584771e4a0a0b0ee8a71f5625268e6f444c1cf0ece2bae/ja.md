```
p6est_partition_ext(p6est_, partition_for_coarsening, weight_fn)
```

森林を再分割します。

森林はプロセッサ間で分割され、各プロセッサはほぼ同数の四分円（または重み）を持ちます。

### パラメータ

  * `p6est`:[in,out] 分割される森林。
  * `partition_for_coarsening`:[in] 真の場合、分割は1レベルの粗化を許可するように修正されます。
  * `weight_fn`:[in] 重み付け関数または均一分割のためのNULL。

### 戻り値

送信された四分円のグローバル数

### プロトタイプ

```c
p4est_gloidx_t p6est_partition_ext (p6est_t * p6est, int partition_for_coarsening, p6est_weight_t weight_fn);
```
