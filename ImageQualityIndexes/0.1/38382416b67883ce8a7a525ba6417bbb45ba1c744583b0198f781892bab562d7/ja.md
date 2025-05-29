```
PSNR <: FullReferenceIQI
assess(PSNR(), x, ref, [, peakval])
assess_psnr(x, ref [, peakval])
```

ピーク信号対雑音比（PSNR）は、ノイズや破損がある場合の画像の品質を測定するために使用されます。

グレイ画像 `x` の場合、PSNR（dB単位）は `10log10(peakval^2/mse(x, ref))` によって計算されます。ここで、`peakval` は画像 `ref` の最大可能ピクセル値です。必要に応じて、`x` は `ref` の型に変換されます。

一般的に、非グレイ画像 `x` の場合、PSNRは `ref` の各チャネルに対して報告され、出力は `Vector` になります。`peakval` もベクトルである必要があります。

!!! info
    従来、`m×n` rgb画像は `m×n×3` グレイ画像として扱われます。rgb画像のチャネルごとのPSNRを計算するには、`peakval` をベクトルとして渡すことができます。例えば、`psnr(x, ref, [1.0, 1.0, 1.0])` のようにします。

