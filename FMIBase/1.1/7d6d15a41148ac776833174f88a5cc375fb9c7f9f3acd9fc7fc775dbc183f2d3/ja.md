```
prepareValueReference(obj, vrs)
```

ここで:

obj ∈ (fmi2ModelDescription, fmi3ModelDescription, FMU2, FMU3, FMU2Component, FMU3Instance) vrs ∈ (fmi2ValueReference, AbstractVector{fmi2ValueReference},         fmi3ValueReference, AbstractVector{fmi3ValueReference},         String, AbstractVector{String},         Integer, AbstractVector{Integer},        :states, :derivatives, :inputs, :outputs, :all, :none,        Nothing)

任意の形式の値参照の1つまたは配列を受け取り（fmi2ValueReferenceFormatを参照）、それをArray{fmi2ValueReference}に変換します（すでにそうでない場合）。
