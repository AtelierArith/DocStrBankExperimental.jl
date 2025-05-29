```
p8est_partition_ext(p8est_, partition_for_coarsening, weight_fn)
```

森林を再分割します。

森林はプロセッサ間で分割され、各プロセッサはほぼ同数の四分木（または重み）を持ちます。

### パラメータ

  * `p8est`:[in,out] 分割される森林。
  * `partition_for_coarsening`:[in] 真の場合、分割は1レベルの粗化を許可するように修正されます。
  * `weight_fn`:[in] 重み付け関数または均一分割のためのNULL。各四分木に対して重み1の定数重み付け関数はweight_fn == NULLと同等ですが、他の定数重み付けは異なる均一分割をもたらす可能性があります。

### 戻り値

出荷された四分木のグローバル数

### プロトタイプ

```c
p4est_gloidx_t p8est_partition_ext (p8est_t * p8est, int partition_for_coarsening, p8est_weight_t weight_fn);
```
