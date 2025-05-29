```
fun_criterion(fun::Function)
```

停止基準関数を作成します。これは、遠いアイテムの数が $\lceil fun(|database|)\rceil$ に達するたびに停止します。すでに定義された例：

```julia
    sqrt_criterion() = fun_criterion(sqrt)
    log2_criterion() = fun_criterion(log2)
```
