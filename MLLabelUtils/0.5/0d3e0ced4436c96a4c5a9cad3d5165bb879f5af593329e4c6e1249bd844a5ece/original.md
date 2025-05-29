```
labelenc(obj) -> LabelEncoding
```

Tries to determine the most approriate label-encoding to describe the given object `obj` based on the result of `label(obj)`. Note that in most cases this function is not typestable.

```
julia> labelenc([:yes,:no,:no,:yes,:maybe])
MLLabelUtils.LabelEnc.NativeLabels{Symbol,3}(Symbol[:yes,:no,:maybe],Dict(:yes=>1,:maybe=>3,:no=>2))

julia> labelenc([1,0,0,1,0,1])
MLLabelUtils.LabelEnc.ZeroOne{Int64,Float64}(0.5)

julia> labelenc(Int8[1,-1,-1,1,-1,1])
MLLabelUtils.LabelEnc.MarginBased{Int8}()
```
