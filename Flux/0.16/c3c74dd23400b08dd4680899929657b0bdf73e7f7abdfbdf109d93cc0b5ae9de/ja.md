```
cpu(m)
```

`m`をCPUにコピーします。これは[`gpu`](@ref)の逆です。構造体に再帰します（Functors.jlのおかげです）。

# 例

```julia-repl
julia> m_gpu = Dense(CUDA.randn(2, 5))
Dense(5 => 2)       # 12パラメータ

julia> m_gpu.bias  # 与えられた重み行列に一致します
2-element CuArray{Float32, 1, CUDA.Mem.DeviceBuffer}:
 0.0
 0.0

julia> m = m_gpu |> cpu
Dense(5 => 2)       # 12パラメータ

julia> m.bias
2-element Vector{Float32}:
 0.0
 0.0
```
