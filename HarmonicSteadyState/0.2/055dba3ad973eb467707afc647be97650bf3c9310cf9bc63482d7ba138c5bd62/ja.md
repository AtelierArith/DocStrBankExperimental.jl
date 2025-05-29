```julia
classify_solutions!(
    res::HarmonicSteadyState.Result,
    func::Union{Function, String},
    name::String;
    physical
) -> Any

```

`res`に関数`func`（Symbolics.jl入力に解析された）を使用して解のクラスを作成します。新しいクラスは`name`でラベル付けされ、`res.classes[name]`に保存されます。デフォルトでは、物理的（実数）解のみが分類され、残りには`false`が返されます。複素解も分類するには、`physical=false`を設定します。

# 例

```julia
# 以前に定義された問題を解く
res = get_steady_states(problem, swept_parameters, fixed_parameters)

# 分類し、結果.classes["large_amplitude"]に保存
classify_solutions!(res, "sqrt(u1^2 + v1^2) > 1.0" , "large_amplitude")
```
