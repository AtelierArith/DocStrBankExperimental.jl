```
imfilter!(r::AbstractResource, imgfilt, img, kernel::Tuple{TriggsSdika...}, border)
imfilter!(r::AbstractResource, imgfilt, img, kernel::TriggsSdika, dim::Integer, border)
```

配列 `img` を Triggs-Sdika 無限インパルス応答 (IIR) `kernel` でフィルタリングし、結果を `imgfilt` に格納します。`FIR` および `FFT` アルゴリズムとは異なり、このバージョンはインプレース操作に安全です。つまり、`imgfilt` は `img` と同じ配列であることができます。

次元ごとに1つのカーネルを指定するか、フィルタリングを行う特定の次元 `dim` を指定します。カーネルを使い果たす前に配列の次元がなくなった場合、残りの次元はフィルタリングされません。

Triggs-Sdika フィルタリングでは、ボーダーオプションは `NA()`, `"replicate"`, または `Fill(value)` のみです。

関連情報: [`imfilter`](@ref), [`KernelFactors.TriggsSdika`](@ref), [`KernelFactors.IIRGaussian`](@ref).
