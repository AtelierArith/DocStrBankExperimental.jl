```
imrotate(arr::AbstractArray{T, 4}, θ; method=:bilinear, rotation_center=size(arr) .÷ 2 .+ 1)
```

配列を最初の2次元で中心ピクセル `rotation_center` の周りに回転させます。`rotation_center` のデフォルト値は、偶数および奇数サイズの配列の整数中心ピクセルが回転するように定義されています。サイズが `(4,4)` の偶数サイズの配列の場合、これは `(3,3)` になります。サイズが `(3,3)` の奇数配列の場合、これは `(2,2)` になります。ただし、`rotation_center` は指定されていれば非整数の数値でも構いません。

角度 `θ` はラジアンで解釈されます。

随伴は ChainRulesCore.jl で定義されています。このメソッドは CUDA でも動作し（原則としてすべての KernelAbstractions.jl サポートバックエンドで動作します）。

# キーワード

  * `method=:bilinear` はバイリニア補間、または `method=:nearest` は最近傍法を意味します。
  * `rotation_center=size(arr) .÷ 2 .+ 1` は、回転する周りに実際の中心ピクセルがあることを意味します。

# 例

```julia-repl
julia> arr = zeros((4,4,1,1)); arr[2,2,1,1] = 1;

julia> arr
4×4×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
 0.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0

julia> NNlib.imrotate(arr, deg2rad(90)) # (3,3) の周りの回転
4×4×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
 0.0  0.0  0.0  0.0
 0.0  0.0  0.0  1.0
 0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0

julia> NNlib.imrotate(arr, deg2rad(90), rotation_center=(2,2))
4×4×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
 0.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0

julia> arr = zeros((3,3,1,1)); arr[1,2,1,1] = 1
1

julia> arr
3×3×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
 0.0  1.0  0.0
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> NNlib.imrotate(arr, deg2rad(45))
3×3×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
 0.0  0.207107  0.0
 0.0  0.0       0.207107
 0.0  0.0       0.0

julia> NNlib.imrotate(arr, deg2rad(45), method=:nearest)
3×3×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
 0.0  0.0  1.0
 0.0  0.0  0.0
 0.0  0.0  0.0
```
