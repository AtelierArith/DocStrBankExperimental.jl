```
struct OptimizeNotCalled <: Exception end
```

[`optimize!`](@ref) が呼び出される前に結果属性を照会できない場合にスローされるエラーです。

## 例

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> objective_value(model)
ERROR: OptimizeNotCalled()
Stacktrace:
[...]
```
