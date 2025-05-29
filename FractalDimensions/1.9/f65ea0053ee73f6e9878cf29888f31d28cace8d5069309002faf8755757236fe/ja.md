# FractalDimensions.jl

[![](https://img.shields.io/badge/docs-dev-lightblue.svg)](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/fractaldimensions/dev/) [![](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/fractaldimensions/stable/) [![](https://img.shields.io/badge/DOI-doi.org/10.1063/5.0160394-purple)](https://pubs.aip.org/aip/cha/article/33/10/102101/2916352/Estimating-fractal-dimensions-A-comparative-review) [![CI](https://github.com/JuliaDynamics/FractalDimensions.jl/workflows/CI/badge.svg)](https://github.com/JuliaDynamics/FractalDimensions.jl/actions?query=workflow%3ACI) [![codecov](https://codecov.io/gh/JuliaDynamics/FractalDimensions.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/JuliaDynamics/FractalDimensions.jl) [![Package Downloads](https://shields.io/endpoint?url=https://pkgs.genieframework.com/api/v1/badge/FractalDimensions)](https://pkgs.genieframework.com?packages=FractalDimensions)

データからフラクタル次元のさまざまな定義を推定するJuliaパッケージで、いわゆる「局所次元と極値指標」を極値理論を通じて含みます。スタンドアロンパッケージとして使用することも、[DynamicalSystems.jl](https://juliadynamics.github.io/DynamicalSystems.jl/dev/)の一部として使用することもできます。

インストールするには、`import Pkg; Pkg.add("FractalDimensions")`を実行してください。

さらなる情報はドキュメントに提供されており、[オンライン](https://juliadynamics.github.io/FractalDimensions.jl/stable/)で見つけるか、`docs/make.jl`ファイルを実行してローカルにビルドすることができます。

*以前は、このパッケージはChaosTools.jlの一部でした。*

## 出版

FractalDimensions.jlは、フラクタル次元のさまざまな推定器を比較するレビュー記事で使用されています。この論文は、パッケージに興味がある場合に関連する読み物である可能性があります。また、パッケージを使用する場合は、論文を引用してください。

```
@article{FractalDimensions.jl,
  doi = {10.1063/5.0160394},
  url = {https://doi.org/10.1063/5.0160394},
  year = {2023},
  month = oct,
  publisher = {{AIP} Publishing},
  volume = {33},
  number = {10},
  author = {George Datseris and Inga Kottlarz and Anton P. Braun and Ulrich Parlitz},
  title = {Estimating fractal dimensions: A comparative review and open source implementations},
  journal = {Chaos: An Interdisciplinary Journal of Nonlinear Science}
}
```
