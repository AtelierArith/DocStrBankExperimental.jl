# DynamicalSystemsBase.jl

[![docsdev](https://img.shields.io/badge/docs-dev-lightblue.svg)](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/dynamicalsystemsbase/dev/) [![docsstable](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/dynamicalsystemsbase/stable/) [![](https://img.shields.io/badge/DOI-10.1007%2F978--3--030--91032--7-purple)](https://link.springer.com/book/10.1007/978-3-030-91032-7) [![CI](https://github.com/JuliaDynamics/DynamicalSystemsBase.jl/workflows/CI/badge.svg)](https://github.com/JuliaDynamics/DynamicalSystemsBase.jl/actions?query=workflow%3ACI) [![codecov](https://codecov.io/gh/JuliaDynamics/DynamicalSystemsBase.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/JuliaDynamics/DynamicalSystemsBase.jl) [![Package Downloads](https://shields.io/endpoint?url=https://pkgs.genieframework.com/api/v1/badge/DynamicalSystemsBase)](https://pkgs.genieframework.com?packages=DynamicalSystemsBase)

`DynamicalSystem` インターフェースと、DynamicalSystems.jl エコシステムで使用される多くの具体的な実装を定義する Julia パッケージです。

インストールするには、`import Pkg; Pkg.add("DynamicalSystemsBase")` を実行します。通常、下流の分析パッケージが再エクスポートするため、`DynamicalSystemsBase` を直接使用することは望ましくありません。

さらなる情報はドキュメントに提供されており、オンラインで見つけるか、`docs/make.jl` ファイルを実行してローカルにビルドすることができます。
