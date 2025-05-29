```
work_precision_adaptive(prob, algs, labels, abstols, reltols, alg_ref;
                        adaptive_ref = false,
                        abstol_ref = 1e-14,
                        reltol_ref = 1e-13,
                        compute_error = rel_max_error_tend,
                        seconds = 2,
                        numruns = 20,
                        kwargs...)
```

`work_precision_adaptive`は、`work_precion_fixed_adaptive`で作成された辞書`dict`に作業精度データを追加します。入力の意味については[`work_precision_adaptive`](@ref)を参照してください。
