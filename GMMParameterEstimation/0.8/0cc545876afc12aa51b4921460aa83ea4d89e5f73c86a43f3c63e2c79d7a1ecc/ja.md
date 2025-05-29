```
build1DSystem(k::Integer, m::Integer, a::Union{Vector{Float64}, Vector{Variable}})
```

1Dガウス混合の多項式システムを構築します。ここで、'm'-1は望ましい最高モーメントであり、`a`は混合係数のベクトルです。
