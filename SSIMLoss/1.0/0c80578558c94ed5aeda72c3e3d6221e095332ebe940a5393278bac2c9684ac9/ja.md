```
ssim(x, y, kernel=ssim_kernel(x); peakval=1, crop=true, dims=:)
```

2つの信号間の[構造的類似性指数](https://en.wikipedia.org/wiki/Structural_similarity)（SSIM）を返します。SSIMは、2つの信号間で計算された統計のスライディングウィンドウの平均を介して計算されます。デフォルトでは、スライディングウィンドウは各信号次元で側面の長さが11のガウス分布であり、σ=1.5です。`crop=false`は、スライディングウィンドウが入力のすべてのピクセルで中心に統計を計算するように`x`と`y`をパディングします（同サイズの畳み込みを介して）。`ssim`は、チャネルおよびバッチ次元にわたって独立して統計を計算します。`x`と`y`は、チャネルおよびバッチ次元を持つ3D/4D/5Dテンソルである可能性があります。

`peakval=1`は画像比較の標準ですが、実際には信号タイプの最大値に設定する必要があります。

`dims`は、計算された統計を平均化する次元を決定します。`dims=1:ndims(x)-1`の場合、SSIMは各バッチ要素ごとに別々に計算されます。

`ssim`の結果は、グレースケールおよびRGB画像（すなわち、グレースケールおよびカラー画像のためにそれぞれサイズが(N1, N2, 1, B)および(N1, N2, 3, B)のx, y）に対する[ImageQualityIndexes](https://github.com/JuliaImages/ImageQualityIndexes.jl)の結果と一致します。

また、[`ssim_loss`](@ref)、[`ssim_loss_fast`](@ref)も参照してください。
