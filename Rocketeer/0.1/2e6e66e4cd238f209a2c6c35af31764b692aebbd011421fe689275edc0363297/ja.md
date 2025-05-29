```julia
RocketModule(
    input_length::Integer,
    n_kernels::Integer
) -> Rocketeer.RocketModule

```

# 概要

特徴の長さとカーネルの数を必要とする新しいRocketModule構造を作成します。

# 引数

  * `input_length::Integer`: カーネル特徴の希望する長さ。
  * `n_kernels::Integer`: 生成するカーネルの希望する数。

# 著作権

## プログラマー

  * Sasha Petrenko <petrenkos@mst.edu> [@AP6YC](https://github.com/AP6YC)

## 元の著者

  * Angus Dempster
  * Francois Petitjean
  * Geoff Webb

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

# メソッドリスト / 定義場所

```julia
RocketModule(input_length, n_kernels)
```

[`packages/Rocketeer/tbPiD/src/lib/rocket.jl:74`](file:///home/terasaki/.julia/packages/Rocketeer/tbPiD/src/lib/rocket.jl)で定義されています。
