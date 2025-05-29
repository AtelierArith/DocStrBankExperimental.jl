```
SSIM([kernel], [(α, β, γ)]; crop=false) <: FullReferenceIQI
assess(iqi::SSIM, img, ref)
assess_ssim(img, ref; crop=false)
```

構造的類似性 (SSIM) 指数は、構造情報の劣化に基づく画像品質評価手法です。

SSIM 指数は、輝度、コントラスト、構造の三つの成分で構成されています； `ssim = 𝐿ᵅ * 𝐶ᵝ * 𝑆ᵞ` であり、ここで `W := (α, β, γ)` は各成分の相対的重要性を制御します。デフォルトでは `W = (1.0, 1.0, 1.0)` です。

実際には、平均版の SSIM が使用されます。各ピクセルで、SSIM は `kernel` によって重み付けされた近傍で局所的に計算され、ssim マップを返します； `ssim` は実際には `mean(ssim_map)` です。デフォルトでは `kernel = KernelFactors.gaussian(1.5, 11)` です。

!!! tip
    デフォルトのパラメータは [1] から来ています。ベンチマーク使用のためには、パラメータを変更しないことをお勧めします。なぜなら、他のほとんどの SSIM 実装が同じ設定に従っているからです。キーワード `crop` は、ssim マップの境界を削除するかどうかを制御します； [1] の結果を再現するには、`true` に設定する必要があります。


# 例

`assess_ssim(img, ref)` は、アルゴリズムのベンチマークを取得するのに十分です。また、カスタム SSIM をインスタンス化し、それを `assess` に渡すか、関数として使用することもできます。例えば：

```julia
iqi = SSIM(KernelFactors.gaussian(2.5, 17), (1.0, 1.0, 2.0))
assess(iqi, img, ref)
iqi(img, ref) # 両方の使用法は同等です
```

!!! info
    SSIM はグレイ画像のみに対して定義されています。`RGB` や他の `Color3` 画像がどのように処理されるかは、異なる実装によって異なる場合があります。`RGB` 画像の場合、チャンネルは 𝐿、𝐶、および 𝑆 を計算する際に別々に処理されます。一般的な `Color3` 画像は、計算の前にまず `RGB` に変換されます。


# 参考文献

[1] Wang, Z., Bovik, A. C., Sheikh, H. R., & Simoncelli, E. P. (2004). Image quality assessment: from error visibility to structural similarity. *IEEE transactions on image processing*, 13(4), 600-612.

[2] Wang, Z., Bovik, A. C., Sheikh, H. R., & Simoncelli, E. P. (2003). The SSIM Index for Image Quality Assessment. Retrived May 30, 2019, from http://www.cns.nyu.edu/~lcv/ssim/
