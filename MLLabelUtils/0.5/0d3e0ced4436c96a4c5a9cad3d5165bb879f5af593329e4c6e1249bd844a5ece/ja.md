```
labelenc(obj) -> LabelEncoding
```

与えられたオブジェクト `obj` を `label(obj)` の結果に基づいて説明するための最も適切なラベルエンコーディングを決定しようとします。この関数はほとんどの場合、型安定ではないことに注意してください。

```
julia> labelenc([:yes,:no,:no,:yes,:maybe])
MLLabelUtils.LabelEnc.NativeLabels{Symbol,3}(Symbol[:yes,:no,:maybe],Dict(:yes=>1,:maybe=>3,:no=>2))

julia> labelenc([1,0,0,1,0,1])
MLLabelUtils.LabelEnc.ZeroOne{Int64,Float64}(0.5)

julia> labelenc(Int8[1,-1,-1,1,-1,1])
MLLabelUtils.LabelEnc.MarginBased{Int8}()
```
