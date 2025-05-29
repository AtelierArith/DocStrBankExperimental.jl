# The2DShapeStructureDataset.jl

[![Static Badge](https://img.shields.io/badge/docs-main-blue)](https://microscopic-image-analysis.github.io/The2DShapeStructureDataset.jl/dev/)

これは[The 2D Shape Structure Dataset](https://2dshapesstructure.github.io/)を扱うための便利なパッケージです。このデータセットには以下の著作権表示があります。

> Copyright (c) [2016] [A. Carlier, K. Leonard, S. Hahmann, G. Morin, M. Collins]


およびMITライセンスの下でライセンスされています。

データセット全体は1.8 MB（圧縮）で、パッケージを使用する際に一度だけダウンロードされます。

## クイックスタート

General Registryからこのパッケージをインストールします：

```julia
julia> ]
pkg> add The2DShapeStructureDataset
```

そして、利用可能にします：

```julia
julia> using The2DShapeStructureDataset
```

例えば、構造`apple-1`の座標を取得することができます：

```julia
julia> shape_coords("apple-1")
2×112 HybridArrays.HybridMatrix{2, StaticArraysCore.Dynamic(), Float64, 2, Matrix{Float64}} with indices SOneTo(2)×Base.OneTo(112):
 0.0      0.0      0.0047847  0.0047847  0.014354  0.019139  0.028708  0.043062  …  0.038278  0.028708  0.019139  0.0095694  0.0047847  0.0      0.0      0.0
 0.41627  0.44498  0.47368    0.50239    0.5311    0.55981   0.58852   0.61722      0.23923   0.26794   0.29665   0.32536    0.35407    0.38278  0.41148  0.41627
```

`shape_names`を呼び出すか、[ビジュアルエクスプローラー](https://2dshapesstructure.github.io/dataset.html)を訪れることで、利用可能な形状を確認できます。
