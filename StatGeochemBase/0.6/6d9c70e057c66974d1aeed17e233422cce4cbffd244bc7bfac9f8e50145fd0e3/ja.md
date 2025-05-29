```julia
imsc(A::AbstractArray, colormap::AbstractVector=viridis, cmin=nanminimum(A), cmax=nanmaximum(A))
```

行列 `A` を指定された `colormap`（デフォルトは `viridis`）を使用して画像（Colors.jl の色の配列）に変換します。オプションで `cmin` と `cmax` の間でスケーリングされます。

### 例

```julia
julia> A = rand(3,3)
3×3 Matrix{Float64}:
 0.39147   0.553489  0.351628
 0.331786  0.343836  0.824674
 0.639233  0.558113  0.965627

julia> img = imsc(A) # N.B. will display as image if `using ImageInTerminal`
3×3 Array{RGB{N0f8},2} with eltype ColorTypes.RGB{FixedPointNumbers.N0f8}:
 RGB{N0f8}(0.282,0.137,0.455)  …  RGB{N0f8}(0.278,0.051,0.376)
 RGB{N0f8}(0.267,0.004,0.329)     RGB{N0f8}(0.431,0.808,0.345)
 RGB{N0f8}(0.133,0.553,0.553)     RGB{N0f8}(0.992,0.906,0.145)

julia> using Images; save("img.png", img) # PNG形式でファイルに保存

julia> using Plots; plot(0:3, 0:3, img) # 指定されたx軸とy軸でプロット
```
