```
hyperparams(names...; prefix="SM_HP_")
```

As per [`hyperparam`](@ref), but taking multiple names and returning a `NamedTuple`.

```jldoctest
using Hyperparameters
ENV["SM_HP_A"] = "5"
ENV["SM_HP_B"] = "1.22"
hyperparams(:a, :b, types=[Int, Float64])

# output
(a = 5, b = 1.22)
```

Also stores the hyperparameters and their values in the global `HYPERPARAMETERS` dictionary.
