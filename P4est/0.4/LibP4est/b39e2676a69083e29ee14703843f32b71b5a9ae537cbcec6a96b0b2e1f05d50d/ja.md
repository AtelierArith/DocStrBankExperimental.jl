```
p4est_partition_for_coarsening(p4est_, num_quadrants_in_proc)
```

正しいパーティションを設定して、1レベルの粗化を可能にします。

### パラメータ

  * `p4est`:[in] パーティションが修正されるフォレスト
  * `num_quadrants_in_proc`:[in,out] 修正されるパーティション

### 戻り値

移動された四分木の絶対数

### プロトタイプ

```c
p4est_gloidx_t p4est_partition_for_coarsening (p4est_t * p4est, p4est_locidx_t * num_quadrants_in_proc);
```
