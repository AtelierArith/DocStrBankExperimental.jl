```
get_attribute(
    model::Union{GenericModel,MOI.OptimizerWithAttributes},
    attr::Union{AbstractString,MOI.AbstractOptimizerAttribute},
)
```

ソルバー特有の属性 `attr` の値を取得します。

これは、関連する MOI モデルで [`MOI.get`](@ref) を呼び出すことと同等です。

`attr` が `AbstractString` の場合、それは [`MOI.RawOptimizerAttribute`](@ref) に変換されます。

## 例

```jldoctest
julia> import HiGHS

julia> opt = optimizer_with_attributes(HiGHS.Optimizer, "output_flag" => true);

julia> model = Model(opt);

julia> get_attribute(model, "output_flag")
true

julia> get_attribute(model, MOI.RawOptimizerAttribute("output_flag"))
true

julia> get_attribute(opt, "output_flag")
true

julia> get_attribute(opt, MOI.RawOptimizerAttribute("output_flag"))
true
```
