```
hyperparams(names...; prefix="SM_HP_")
```

[`hyperparam`](@ref)に従って、複数の名前を受け取り、`NamedTuple`を返します。

```jldoctest
using Hyperparameters
ENV["SM_HP_A"] = "5"
ENV["SM_HP_B"] = "1.22"
hyperparams(:a, :b, types=[Int, Float64])

# output
(a = 5, b = 1.22)
```

また、ハイパーパラメータとその値をグローバルな`HYPERPARAMETERS`辞書に保存します。
