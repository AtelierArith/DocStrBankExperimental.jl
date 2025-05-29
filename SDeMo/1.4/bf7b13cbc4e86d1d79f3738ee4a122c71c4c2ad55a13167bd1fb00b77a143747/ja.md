```
MultivariateTransform{T} <: Transformer
```

`T` は多変量変換であり、`MultivariateStats` パッケージを通じて提供される可能性があります。現在サポートされている変換は `PCA`、`PPCA`、`KernelPCA`、および `Whitening` であり、それらは型エイリアス (*例* `PCATransform`) を通じて文書化されています。
