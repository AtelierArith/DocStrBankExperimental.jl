```julia
struct RocketKernel
```

# 概要

1つのロケットカーネルに関する情報を含む構造体。

# 著作権

## プログラマー

  * サーシャ・ペトレンコ <petrenkos@mst.edu> [@AP6YC](https://github.com/AP6YC)

## 元の著者

  * アンガス・デンプスター
  * フランソワ・プティジャン
  * ジェフ・ウェッブ

## Bibtexエントリ

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

  * `length::Int64`: カーネルの長さ。
  * `weight::Vector{Float64}`: 特徴に対応する重みのベクトル。
  * `bias::Float64`: 構築中に計算された内部ロケットバイアスパラメータ。
  * `dilation::Int64`: 構築中に計算された内部ロケット拡張パラメータ。
  * `padding::Int64`: 構築中に計算された内部ロケットパディングパラメータ。
