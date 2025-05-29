```
SetVariableBounds(p::DSProblem{T}, l::Vector{T}, u::Vector{T}) where T
```

各変数に対して[`SetVariableBound`](@ref)を呼び出します。ベクトル`l`と`u`は、それぞれの変数の下限と上限を含む必要があります。
