```
fun_criterion(fun::Function)
```

Creates a stop-criterion function that stops whenever the number of far items reaches $\lceil fun(|database|)\rceil$. Already defined examples:

```julia
    sqrt_criterion() = fun_criterion(sqrt)
    log2_criterion() = fun_criterion(log2)
```
