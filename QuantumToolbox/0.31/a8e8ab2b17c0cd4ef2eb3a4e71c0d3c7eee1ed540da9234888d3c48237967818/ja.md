```
struct Dimensions{N,T<:Tuple} <: AbstractDimensions{N, N}
    to::T
end
```

各サブシステムのヒルベルト [`Space`](@ref) を記述する構造体。
