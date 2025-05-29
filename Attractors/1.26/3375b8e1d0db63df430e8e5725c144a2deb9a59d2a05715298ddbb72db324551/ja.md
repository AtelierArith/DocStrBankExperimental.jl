# Attractors.jl

[![docsdev](https://img.shields.io/badge/docs-dev-lightblue.svg)](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/attractors/dev/) [![docsstable](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/attractors/stable/) [![Paper](https://img.shields.io/badge/Cite-DOI:10.1063/5.0159675-purple)](https://doi.org/10.1063/5.0159675) [![CI](https://github.com/JuliaDynamics/Attractors.jl/workflows/CI/badge.svg)](https://github.com/JuliaDynamics/Attractors.jl/actions?query=workflow%3ACI) [![codecov](https://codecov.io/gh/JuliaDynamics/Attractors.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/JuliaDynamics/Attractors.jl) [![Package Downloads](https://img.shields.io/badge/dynamic/json?url=http%3A%2F%2Fjuliapkgstats.com%2Fapi%2Fv1%2Ftotal_downloads%2FAttractors&query=total_requests&label=Downloads)](http://juliapkgstats.com/pkg/Attractors)

Attractors.jlは、以下のためのJuliaパッケージです。

  * 任意の動的システムのすべてのアトラクタおよびすべてのタイプのアトラクタを見つけること。拡張可能なインターフェースにより、アトラクタを見つけるための新しいアルゴリズムを追加できます。
  * アトラクタの吸引盆地や、盆地の状態空間の割合を見つけること。これには、出口盆地（無限大への発散）を見つけることが含まれます。
  * アトラクタの非局所的安定性（グローバル安定性またはレジリエンスとも呼ばれる）を分析すること。
  * パラメータ範囲にわたるアトラクタとその盆地（または他の安定性の指標）の**グローバル継続**を実行すること。グローバル継続は、従来の局所継続（AUTO、MatCont、BifurcationKit.jlなど）に対していくつかの利点を提供する新しい最先端の継続のタイプです。詳細はドキュメントの比較を参照してください。
  * 盆地の境界とエッジ状態を見つけ、それらのフラクタル特性を分析すること。
  * 知られた動的ルールを持つシステムに関連するティッピングポイント機能。
  * そしてもっと！

これはスタンドアロンパッケージとして使用することも、[DynamicalSystems.jl](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/dynamicalsystems/stable/)の一部として使用することもできます。

インストールするには、`import Pkg; Pkg.add("Attractors")`を実行してください。

すべての詳細情報はドキュメントに提供されており、[オンライン](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/attractors/stable/)で見つけるか、`docs/make.jl`ファイルを実行してローカルにビルドできます。

*以前は、Attractors.jlはChaosTools.jlの一部でした*
