`Rocketeer.jl`パッケージのメインモジュール。

# 帰属

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

# インポート

次の名前は、パッケージによって依存関係としてインポートされます:

  * `Base`
  * `Core`
  * `DocStringExtensions`
  * `NumericalTypeAliases`
  * `Pkg`
  * `Random`

# エクスポート

次の名前はエクスポートされ、パッケージを`using`したときに利用可能です:

  * [`ROCKETEER_VERSION`](@ref)
  * [`RocketKernel`](@ref)
  * [`RocketModule`](@ref)
  * [`apply_kernel`](@ref)
  * [`apply_kernels`](@ref)
  * [`load_rocket`](@ref)
  * [`save_rocket`](@ref)
