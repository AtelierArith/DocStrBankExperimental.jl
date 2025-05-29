```
p6est_partition(p6est_, weight_fn)
```

森林を均等に分割します。

森林はプロセッサ間で分割され、各プロセッサはほぼ同じ数の四分円を持つことになります。

この呼び出し中に `p6est`->layers および `p6est`->global*first*layers が変更される可能性があることに注意してください。[`p6est_partition`](@ref) が呼び出される前にこれらのオブジェクトを参照しているポインタは無効になります。

### パラメータ

  * `p6est`:[in,out] 分割される森林。
  * `weight_fn`:[in] 重み付け関数または均等分割のための NULL。

### プロトタイプ

```c
p4est_gloidx_t p6est_partition (p6est_t * p6est, p6est_weight_t weight_fn);
```
