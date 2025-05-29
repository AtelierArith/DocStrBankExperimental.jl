```
applymergetruncate!(gate, psum, aux_psum, thetas, param_idx; max_weight=Inf, min_abs_coeff=1e-10, max_freq=Inf, max_sins=Inf, customtruncfunc=nothing, kwargs...)
```

`propagate!`の下にある1階層の関数で、`psum`内のすべてのパウリ文字列に対して1つのゲートを適用し、必要に応じて`aux_psum`を使用し、すべてを`psum`に戻してマージします。マージ後にここで切り捨てがチェックされます。この関数は、下位の関数`applytoall!`、`applyandadd!`、および`apply`が不十分な場合にカスタムゲートのために上書きすることができます。
