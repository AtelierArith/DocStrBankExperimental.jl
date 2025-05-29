```julia
mutable struct ILMSystem{static, PT, N, PHT, BCF, FF, DTF, MTF, BCT, ECT}
```

浸漬層問題のための演算子とキャッシュのシステムです。これは[`construct_system`](@ref)によって構築されます。
