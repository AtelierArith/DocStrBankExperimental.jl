```
MSSSIM([kernel], [W]; num_scales = length(W)) <: FullReferenceIQI
assess(iqi::MSSSIM, img, ref)
assess_msssim(img, ref; num_scales = 5)
```

2つの画像間のマルチスケール構造類似性（MS-SSIM）を計算します。

!!! tip
    デフォルトのパラメータは[1]から来ています。ベンチマーク使用のためには、ほとんどの他のSSIM実装が同じ設定に従うため、パラメータを変更しないことをお勧めします。


# 例

ベンチマーク使用のためには、`assess_msssim(img, ref)`を使用することをお勧めします。また、カスタムの`MSSSIM`インスタンスを作成し、それを`assess`に渡すか、関数として使用することもできます。

```julia
iqi = MSSSIM(KernelFactors.gaussian(2.5, 17), (1.0, 1.0, 2.0)./4)
assess(iqi, img, ref)
iqi(img, ref) # 両方の使用法は同等です
```

# 参考文献

[1] Wang, Z., Simoncelli, E. P., & Bovik, A. C. (2003, November). Multiscale structural similarity for image quality assessment.In *The Thrity-Seventh Asilomar Conference on Signals, Systems & Computers*, 2003 (Vol. 2, pp. 1398-1402). Ieee.

[2] Wang, Z. IW-SSIM: Information Content Weighted Structural Similarity Index for Image Quality Assessment. Retrived July 9, 2020, from https://ece.uwaterloo.ca/~z70wang/research/iwssim/

[3] Jorge Pessoa. pytorch-msssim. Retrived July 9, 2020, from https://github.com/jorge-pessoa/pytorch-msssim
