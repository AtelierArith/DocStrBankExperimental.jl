```
work_precision_fixed!(dict, prob, algs, labels, dts, alg_ref;
                      compute_error = rel_max_error_tend,
                      seconds = 2,
                      numruns = 20)
)
```

`work_precision_fixed`で作成された辞書`dict`に作業精度データを追加します。入力の意味については[`work_precision_fixed`](@ref)を参照してください。
