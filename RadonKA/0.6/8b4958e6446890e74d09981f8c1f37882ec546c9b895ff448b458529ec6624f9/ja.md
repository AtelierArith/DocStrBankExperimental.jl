```
radon(I, θs; <kwargs>)
```

抽象配列 `I` の平行ラドン変換を計算します。直感的には、`radon` は `I` の配列エントリをレイパスに沿って合計します。

最初の2次元は y と x です。3次元は z、回転軸です。`size(I, 1)` と `size(I, 2)` は等しくなければなりません。ラドン変換はピクセル `size(I, 1) ÷ 2 + 1` の周りで回転するため、常に整数の中心ピクセルがあります！`AbstractArray{T, 3}` または `AbstractArray{T, 2}` で動作します。

`θs` はラジアンで角度を格納するベクトルまたは範囲です。

原則として、KernelAbstractions.jl のすべてのバックエンドは動作するはずですが、テストされていません。CUDA と CPU 配列は積極的にテストされています。`radon` と [`backproject`](@ref) は `I` に関して微分可能です。

# キーワード

## `μ=nothing` - 減衰ラドン変換

`μ != nothing` の場合、レイは `exp(-μ * dist)` で減衰されます。ここで `dist` は視野の円形境界までの距離です。`μ` はピクセル長の単位です。したがって、`μ=1` は1ピクセルを通過した場合の減衰 `exp(-1)` に対応します。`isnothing(μ)` の場合、レイは減衰されません。

`μ` は `I` と同じサイズの配列でもあり、空間的に変化する減衰を可能にします。たとえば、`μ=0.01` と `μ = ones(size(I)) * 0.01` は同等です。実際には、減衰の計算方法が異なるため、わずかな違いがあります。

## `geometry = RadonParallelCircle(-(size(img,1)-1)÷2:(size(img,1)-1)÷2)`

これは平行ラドン変換に対応します。ジオメトリの完全なリストについては `?RadonGeometries` を参照してください。また、非常に柔軟な `RadonFlexibleCircle` もあります。

[`backproject`](@ref) も参照してください。

# 例

対角線レイ `π/4` に対してシノグラムが値 `1.41421` を持つ理由は、そのような対角線がピクセルを通過する際により長い距離を移動するためです。

```jldoctest
julia> arr = zeros((4,4)); arr[3,3] = 1;

julia> radon(arr, [0, π/4, π/2])
3×3 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 0.0  0.0      0.0
 1.0  1.41421  1.0
 0.0  0.0      0.0
```

## 異なる検出器を選択

```jldoctest
julia> array = ones((6,6))
6×6 Matrix{Float64}:
 1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0

julia> radon(array, [0])
5×1 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 1.0
 3.7320508075688767
 5.0
 3.7320508075688767
 1.0

julia> radon(array, [0], geometry=RadonParallelCircle(6, -2:2))
5×1 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 1.0
 3.7320508075688767
 5.0
 3.7320508075688767
 1.0

julia> radon(array, [0], geometry=RadonParallelCircle(6, -2:2:2))
3×1 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 1.0
 5.0
 1.0
```

## レイにいくつかの重みを適用

```jldoctest
julia> array = ones((6,6));

julia> radon(array, [0], geometry=RadonParallelCircle(6, -2:2, [2,1,0,1,2]))
5×1 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 2.0
 3.7320508075688767
 0.0
 3.7320508075688767
 2.0
```
