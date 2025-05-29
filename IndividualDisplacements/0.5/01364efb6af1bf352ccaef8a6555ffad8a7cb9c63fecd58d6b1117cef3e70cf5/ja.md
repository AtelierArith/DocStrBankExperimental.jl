```
FlowFields(; u::Union{Array,Tuple}=[], v::Union{Array,Tuple}=[], w::Union{Array,Tuple}=[], 
period::Union{Array,Tuple}=[], gridtype::Symbol=:centered)
```

キーワードに基づいてFlowFieldsデータ構造を構築します。

```
uC, vC, _ = SimpleFlowFields(16)
F=FlowFields(u=uC,v=vC,period=(0,10.))
```
