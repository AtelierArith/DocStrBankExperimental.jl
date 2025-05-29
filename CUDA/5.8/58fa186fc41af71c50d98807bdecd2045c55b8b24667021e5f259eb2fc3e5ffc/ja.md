```
cu(A; unified=false)
```

意見のあるGPU配列アダプタで、配列の要素型 `T` を変更する場合があります：

  * `T<:AbstractFloat` の場合、パフォーマンスの理由から `CuArray{Float32}` を作成します。（ただし、`Float16` および `BFloat16` の要素型は変更されません。）
  * `T<:Complex{<:AbstractFloat}` の場合、`CuArray{ComplexF32}` を作成します。
  * その他の `isbitstype(T)` の場合、`CuArray{T}` を作成します。

対照的に、`CuArray(A)` は要素型を変更しません。

いくつかのラッパー構造体の内部で動作するために Adapt.jl を使用します。

# 例

```
julia> cu(ones(3)')
1×3 adjoint(::CuArray{Float32, 1, CUDA.DeviceMemory}) with eltype Float32:
 1.0  1.0  1.0

julia> cu(zeros(1, 3); unified=true)
1×3 CuArray{Float32, 2, CUDA.UnifiedMemory}:
 0.0  0.0  0.0

julia> cu(1:3)
1:3

julia> CuArray(ones(3)')  # Adjointを無視し、Float64を保持
1×3 CuArray{Float64, 2, CUDA.DeviceMemory}:
 1.0  1.0  1.0

julia> adapt(CuArray, ones(3)')  # これによりAdjointラッパーが復元されます
1×3 adjoint(::CuArray{Float64, 1, CUDA.DeviceMemory}) with eltype Float64:
 1.0  1.0  1.0

julia> CuArray(1:3)
3-element CuArray{Int64, 1, CUDA.DeviceMemory}:
 1
 2
 3
```
