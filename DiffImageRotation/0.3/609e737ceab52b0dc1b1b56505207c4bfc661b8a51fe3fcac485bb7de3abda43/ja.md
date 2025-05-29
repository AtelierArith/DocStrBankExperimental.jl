```
imrotate(arr::AbstractArray, θ; method=:bilinear, midpoint=size(arr) .÷ 2 .+ 1)
```

行列を中心ピクセル `midpoint` の周りで回転させます。角度 `θ` はラジアンで解釈されます。

随伴は ChainRulesCore.jl で定義されています。このメソッドは CUDA でも動作します（原則としてすべての KernelAbstractions.jl がサポートするバックエンドで動作します）。`arr` が `AbstractArray{T, 3}` の場合、第三次元はバッチ次元として解釈されます。

# キーワード

  * `method=:bilinear` はバイリニア補間、または `method=:nearest` は最近傍法を指定します。
  * `midpoint=size(arr) .÷ 2 .+ 1` は常に回転する実際の中心ピクセルがあることを意味します。

# 例

```julia-repl
julia> arr = zeros((6, 6)); arr[3:4, 4] .= 1;

julia> arr
6×6 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  1.0  0.0  0.0
 0.0  0.0  0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0

julia> imrotate(arr, deg2rad(45))
6×6 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 0.0  0.0  0.0        0.0        0.0       0.0
 0.0  0.0  0.0        0.0        0.0       0.0
 0.0  0.0  0.0        0.292893   0.585786  0.0
 0.0  0.0  0.0857864  1.0        0.292893  0.0
 0.0  0.0  0.0        0.0857864  0.0       0.0
 0.0  0.0  0.0        0.0        0.0       0.0

julia> imrotate(arr, deg2rad(90))
6×6 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 0.0  0.0  0.0  0.0  0.0          0.0
 0.0  0.0  0.0  0.0  0.0          0.0
 0.0  0.0  0.0  0.0  1.11022e-16  0.0
 0.0  0.0  0.0  1.0  1.0          0.0
 0.0  0.0  0.0  0.0  0.0          0.0
 0.0  0.0  0.0  0.0  0.0          0.0

julia> imrotate(arr, deg2rad(90), midpoint=(3,3))
6×6 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  1.0  1.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0

julia> imrotate(arr, deg2rad(90), method=:nearest)
6×6 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  1.0  1.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0

julia> using CUDA

julia> Array(imrotate(CuArray(arr), deg2rad(90))) ≈ imrotate(arr, deg2rad(90))
true

julia> using Zygote

julia> f(x) = sum(abs2.(imrotate(x, π/4)))
f (generic function with 1 method)

julia> Zygote.gradient(f, arr)
([0.0 0.0 … 0.0 0.0; 0.0 0.0 … 5.387705551013979e-17 0.0; … ; 0.0 0.0 … 0.08578643762690495 0.0; 0.0 0.0 … 0.0 0.0],)

```
