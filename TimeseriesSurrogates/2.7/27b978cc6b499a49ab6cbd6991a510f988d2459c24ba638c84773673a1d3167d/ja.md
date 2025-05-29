# TimeseriesSurrogates.jl

[![docsdev](https://img.shields.io/badge/docs-dev-lightblue.svg)](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/timeseriessurrogates/dev/) [![docsstable](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/timeseriessurrogates/stable/) [![](https://img.shields.io/badge/DOI-10.21105/joss.04414-purple)](https://doi.org/10.21105/joss.04414) [![CI](https://github.com/JuliaDynamics/TimeseriesSurrogates.jl/workflows/CI/badge.svg)](https://github.com/JuliaDynamics/TimeseriesSurrogates.jl/actions?query=workflow%3ACI) [![codecov](https://codecov.io/gh/JuliaDynamics/TimeseriesSurrogates.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/JuliaDynamics/TimeseriesSurrogates.jl) [![Package Downloads](https://shields.io/endpoint?url=https://pkgs.genieframework.com/api/v1/badge/TimeseriesSurrogates)](https://pkgs.genieframework.com?packages=TimeseriesSurrogates)

時系列サロゲートを生成するためのJuliaパッケージです。TimeseriesSurrogates.jlは、時系列サロゲートを生成するための最も高速で機能豊富なオープンソースコードです。スタンドアロンパッケージとして使用することも、DynamicalSystems.jlやCausalityTools.jlなどのJuliaDynamicsの他のプロジェクトの一部として使用することもできます。

インストールするには、`import Pkg; Pkg.add("TimeseriesSurrogates")`を実行してください。

さらなる情報は、オンラインで見つけるか、`docs/make.jl`ファイルを実行してローカルにビルドすることで提供されるドキュメントに記載されています。

## 引用

TimeseriesSurrogates.jlを引用するには、以下のBiBTeXエントリまたはDOIを使用してください：

DOI: https://doi.org/10.21105/joss.04414

BiBTeX:

```latex
@article{TimeseriesSurrogates.jl,
    doi = {10.21105/joss.04414},
    url = {https://doi.org/10.21105/joss.04414},
    year = {2022},
    publisher = {The Open Journal},
    volume = {7},
    number = {77},
    pages = {4414},
    author = {Kristian Agasøster Haaga and George Datseris},
    title = {TimeseriesSurrogates.jl: a Julia package for generating surrogate data},
    journal = {Journal of Open Source Software}
}
```
