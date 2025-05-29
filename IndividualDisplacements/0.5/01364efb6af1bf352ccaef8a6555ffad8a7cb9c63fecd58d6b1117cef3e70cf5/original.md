```
FlowFields(; u::Union{Array,Tuple}=[], v::Union{Array,Tuple}=[], w::Union{Array,Tuple}=[], 
period::Union{Array,Tuple}=[], gridtype::Symbol=:centered)
```

Construct FlowFields data structure based on keywords.

```
uC, vC, _ = SimpleFlowFields(16)
F=FlowFields(u=uC,v=vC,period=(0,10.))
```
