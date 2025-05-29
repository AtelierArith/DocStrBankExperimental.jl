```
raw_status(model::GenericModel)
```

ソルバーが停止した理由をその言葉で返します（すなわち、MathOptInterfaceモデル属性 [`MOI.RawStatusString`](@ref)）。

## 例

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> raw_status(model)
"optimize not called"
```
