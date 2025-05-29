```
p4est_partition_ext(p4est_, partition_for_coarsening, weight_fn)
```

フォレストを再分割します。

フォレストはプロセッサ間で分割され、各プロセッサはほぼ同数の四分木（または重み）を持ちます。

### パラメータ

  * `p4est`:[in,out] 分割されるフォレスト。
  * `partition_for_coarsening`:[in] trueの場合、分割は1レベルの粗化を許可するように修正されます。
  * `weight_fn`:[in] 重み付け関数または均一分割のためのNULL。各四分木に対して重み1の定数重み付け関数はweight_fn == NULLと同等ですが、他の定数重み付けは異なる均一分割をもたらす可能性があります。

### 戻り値

出荷された四分木のグローバル数

### プロトタイプ

```c
p4est_gloidx_t p4est_partition_ext (p4est_t * p4est, int partition_for_coarsening, p4est_weight_t weight_fn);
```
