```
set_attribute(
    model::Union{GenericModel,MOI.OptimizerWithAttributes},
    attr::Union{AbstractString,MOI.AbstractOptimizerAttribute},
    value,
)
```

ソルバー特有の属性 `attr` の値を `value` に設定します。

これは、関連する MOI モデルで [`MOI.set`](@ref) を呼び出すことと同等です。

`attr` が `AbstractString` の場合、それは [`MOI.RawOptimizerAttribute`](@ref) に変換されます。

## 例

```jldoctest
julia> import HiGHS

julia> opt = optimizer_with_attributes(HiGHS.Optimizer, "output_flag" => false);

julia> model = Model(opt);

julia> set_attribute(model, "output_flag", false)

julia> set_attribute(model, MOI.RawOptimizerAttribute("output_flag"), true)

julia> set_attribute(opt, "output_flag", true)

julia> set_attribute(opt, MOI.RawOptimizerAttribute("output_flag"), false)
```
