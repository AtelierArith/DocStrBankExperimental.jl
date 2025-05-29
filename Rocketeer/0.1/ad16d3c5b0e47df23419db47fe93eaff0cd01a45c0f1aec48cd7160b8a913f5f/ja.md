```julia
struct RocketModule
```

# 概要

[`RocketKernel`](@ref)sのベクターを含む構造体です。

# 著作権

## プログラマー

  * Sasha Petrenko <petrenkos@mst.edu> [@AP6YC](https://github.com/AP6YC)

## 元の著者

  * Angus Dempster
  * Francois Petitjean
  * Geoff Webb

## Bibtex エントリ

```bibtex
@article{dempster_etal_2020,
    author  = {Dempster, Angus and Petitjean, Francois and Webb, Geoffrey I},
    title   = {ROCKET: Exceptionally fast and accurate time classification using random convolutional kernels},
    year    = {2020},
    journal = {Data Mining and Knowledge Discovery},
    doi     = {https://doi.org/10.1007/s10618-020-00701-z}
}
```

## 引用リンク

  * 論文:

      * [ジャーナル記事](https://link.springer.com/article/10.1007/s10618-020-00701-z) ([DOI](https://doi.org/10.1007/s10618-020-00701-z))
      * [プレプリント](https://arxiv.org/abs/1910.13051)
  * ソフトウェア

      * [rocket](https://github.com/angus924/rocket) (Python)

# フィールド

  * `input_length::Int64`: [`RocketKernel`](@ref)sを生成するために使用される入力の長さ。
  * `kernels::Vector{Rocketeer.RocketKernel}`: 完全なロケットモジュールを構成する[`RocketKernel`](@ref)sのリスト。
