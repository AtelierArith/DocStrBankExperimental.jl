`ConvergenceTest` 抽象型は、反復が収束したかどうかを判断するメカニズムを表します。

```
converged(ct::ConvergenceTest, meas::Vector{KRatio}, computed::Dict{Element,<:AbstractFloat})::Bool
```
