```
SSIM([kernel], [(α, β, γ)]) <: FullReferenceIQI
assess(iqi::SSIM, img, ref)
assess_ssim(img, ref)
```

構造的類似性 (SSIM) 指数は、構造情報の劣化に基づく画像品質評価手法です。

SSIM 指数は、輝度、コントラスト、構造の三つの成分で構成されています。`ssim = 𝐿ᵅ * 𝐶ᵝ * 𝑆ᵞ` であり、ここで `W := (α, β, γ)` は各成分の相対的重要性を制御します。デフォルトでは `W = (1.0, 1.0, 1.0)` です。

実際には、平均バージョンの SSIM が使用されます。各ピクセルで、SSIM は `kernel` によって重み付けされた近傍で局所的に計算され、ssim マップを返します。実際の `ssim` は `mean(ssim_map)` です。デフォルトでは `kernel = KernelFactors.gaussian(1.5, 11)` です。

!!! info
    SSIM はグレイ画像に対してのみ定義されています。RGB 画像は 3D グレイ画像として扱われます。一般的な `Color3` 画像は最初に RGB 画像に変換されます。この場合、RGB に変換されるのを避けたい場合は、`channelview` を使用して手動で拡張できます。


# 例

`ssim(img, ref)` はアルゴリズムのベンチマークを取得するのに十分です。また、カスタム SSIM をインスタンス化し、それを `assess` に渡すか、関数として使用することもできます。例えば：

```julia
iqi = SSIM(KernelFactors.gaussian(2.5, 17), (1.0, 1.0, 2.0))
assess(iqi, img, ref)
iqi(img, ref)
```

# 参考文献

[1] Wang, Z., Bovik, A. C., Sheikh, H. R., & Simoncelli, E. P. (2004). Image quality assessment: from error visibility to structural similarity. *IEEE transactions on image processing*, 13(4), 600-612.

[2] Wang, Z., Bovik, A. C., Sheikh, H. R., & Simoncelli, E. P. (2003). The SSIM Index for Image Quality Assessment. Retrived May 30, 2019, from http://www.cns.nyu.edu/~lcv/ssim/
