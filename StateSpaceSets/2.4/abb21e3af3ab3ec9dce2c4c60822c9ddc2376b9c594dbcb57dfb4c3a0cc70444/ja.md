# StateSpaceSets.jl

[![docsdev](https://img.shields.io/badge/docs-dev-lightblue.svg)](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/statespacesets/dev/) [![docsstable](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/statespacesets/stable/) [![](https://img.shields.io/badge/DOI-10.1007%2F978--3--030--91032--7-purple)](https://link.springer.com/book/10.1007/978-3-030-91032-7) [![CI](https://github.com/JuliaDynamics/StateSpaceSets.jl/workflows/CI/badge.svg)](https://github.com/JuliaDynamics/StateSpaceSets.jl/actions?query=workflow%3ACI) [![codecov](https://codecov.io/gh/JuliaDynamics/StateSpaceSets.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/JuliaDynamics/StateSpaceSets.jl)

状態空間セットの機能を提供するJuliaパッケージです。これらは固定長（次元と呼ばれる）の点の順序付きコレクションです。これは、JuliaDynamics組織の多くの他のパッケージによって使用されています。`StateSpaceSets`の主なエクスポートは、具体的な型`StateSpaceSet`です。このパッケージは、距離、隣接検索、サンプリング、および正規化の機能も提供します。

これをインストールするには、`import Pkg; Pkg.add("StateSpaceSets")`を実行できますが、このパッケージはそれを使用するすべての下流パッケージによって再エクスポートされるため、直接インストールする理由は実際にはありません。
