# BSeries

[![Docs-stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://ranocha.de/BSeries.jl/stable) [![Docs-dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://ranocha.de/BSeries.jl/dev) [![Build Status](https://github.com/ranocha/BSeries.jl/workflows/CI/badge.svg)](https://github.com/ranocha/BSeries.jl/actions?query=workflow%3ACI) [![Coveralls](https://coveralls.io/repos/github/ranocha/BSeries.jl/badge.svg?branch=main)](https://coveralls.io/github/ranocha/BSeries.jl?branch=main) [![Codecov](https://codecov.io/gh/ranocha/BSeries.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/ranocha/BSeries.jl) [![License: MIT](https://img.shields.io/badge/License-MIT-success.svg)](https://opensource.org/licenses/MIT) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.5534602.svg)](https://doi.org/10.5281/zenodo.5534602)

[B-series](https://en.wikipedia.org/wiki/Butcher_group)に関する機能のコレクションです。[Julia](https://julialang.org/)で実装されています。詳細は以下を参照してください。

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)

## API Documentation

[BSeries.jl](https://github.com/ranocha/BSeries.jl)のAPIは[オンラインドキュメント](https://ranocha.de/BSeries.jl/stable)に記載されています。各関数に関する情報はそのドキュメンテーション文字列にあります。

BSeries.jlは[RootedTrees.jl](https://github.com/SciML/RootedTrees.jl)からすべてを再エクスポートします。ただし、そのパッケージの機能に依存する場合は、破壊的変更を追跡するために、プロジェクトの依存関係に明示的に含める必要があります。RootedTrees.jlとBSeries.jlのバージョン番号は必ずしも同期していないためです。

BSeries.jlの主なAPIは以下のコンポーネントで構成されています。

  * B-seriesは、`RootedTree`を係数にマッピングする`AbstractDict`のように振る舞います。
  * ルンゲ・クッタ法などの時間積分法のB-seriesは、`bseries`関数によって構築できます。
  * ベクトル空間の演算（加算/減算およびスカラーによる乗算）が利用可能です。
  * 合成法則と代入法則の代数構造は、`compose`および`substitute`を介して実装されています。
  * 逆誤差解析は、`modified_equation`および`modifying_integrator`を介して実行できます。

詳細については、ドキュメントまたはドキュメンテーション文字列を参照してください。

B-series分析は、常微分方程式（ODE）の自律形式に最も便利に適用されることに注意してください。したがって、BSeries.jlとRootedTrees.jlは通常、時間積分法がODEが自律形式で書かれているか非自律形式で書かれているかに関係なく、同じ結果を出すと仮定しています。ルンゲ・クッタ法の場合、これは通常の行和仮定が使用されることを意味します。

## Referencing

[BSeries.jl](https://github.com/ranocha/BSeries.jl)を研究に使用する場合は、以下のbibtexエントリを使用して引用してください。

```bibtex
@article{ketcheson2023computing,
  title={Computing with {B}-series},
  author={Ketcheson, David I and Ranocha, Hendrik},
  journal={ACM Transactions on Mathematical Software},
  volume={49},
  number={2},
  year={2023},
  month={06},
  doi={10.1145/3573384},
  eprint={2111.11680},
  eprinttype={arXiv},
  eprintclass={math.NA}
}
```

さらに、BSeries.jlを直接参照することもできます。

```bibtex
@misc{ranocha2021bseries,
  title={{BSeries.jl}: {C}omputing with {B}-series in {J}ulia},
  author={Ranocha, Hendrik and Ketcheson, David I},
  year={2021},
  month={09},
  howpublished={\url{https://github.com/ranocha/BSeries.jl}},
  doi={10.5281/zenodo.5534602}
}
```

## License and contributing

このプロジェクトはMITライセンスの下でライセンスされています（[License](@ref)を参照）。オープンソースプロジェクトであるため、コミュニティからの貢献を非常に歓迎します。詳細については[Contributing](@ref)を参照してください。
