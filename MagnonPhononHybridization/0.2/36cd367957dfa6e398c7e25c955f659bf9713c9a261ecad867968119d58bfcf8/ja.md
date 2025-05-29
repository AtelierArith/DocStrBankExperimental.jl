```
DMHybridization(id::Symbol, value, bondkind; amplitude::Union{Function, Nothing}=nothing, ismodulatable::Union{Function, Bool}=true)
```

DMマグノン-フォノン結合項。

`Term{:DMHybridization, id, V, B, C<:TermCoupling, A<:TermAmplitude}` の型エイリアス。
