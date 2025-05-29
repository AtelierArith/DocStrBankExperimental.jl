```
add_infinite_model_optimizer(opt_model::JuMP.Model, inf_model::InfiniteModel)
```

現在の最適化器とその属性を `inf_model` に関連付けて解析し、それらを `opt_model` にロードします。これは [`set_optimizer_model`](@ref) の内部メソッドとして使用されることを意図しています。
