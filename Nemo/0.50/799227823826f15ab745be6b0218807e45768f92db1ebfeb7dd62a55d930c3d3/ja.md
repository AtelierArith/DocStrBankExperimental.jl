```
set_precision!(::Type{Balls}, n::Int)
```

すべてのボール演算の精度を `n` に設定します。

# 例

```julia
julia> const_pi(RealField())
[3.141592653589793239 +/- 5.96e-19]

julia> set_precision!(Balls, 200); const_pi(RealField())
[3.14159265358979323846264338327950288419716939937510582097494 +/- 5.73e-60]
```
