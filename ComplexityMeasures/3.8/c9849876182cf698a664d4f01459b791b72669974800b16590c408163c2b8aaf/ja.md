# ComplexityMeasures.jl

[![docsdev](https://img.shields.io/badge/docs-dev-lightblue.svg)](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/complexitymeasures/dev/) [![docsstable](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/complexitymeasures/stable/) [![CI](https://github.com/juliadynamics/ComplexityMeasures.jl/workflows/CI/badge.svg)](https://github.com/JuliaDynamics/ComplexityMeasures.jl/actions) [![codecov](https://codecov.io/gh/JuliaDynamics/ComplexityMeasures.jl/branch/main/graph/badge.svg?token=6XlPGg5nRG)](https://codecov.io/gh/JuliaDynamics/ComplexityMeasures.jl) [![Package Downloads](https://img.shields.io/badge/dynamic/json?url=http%3A%2F%2Fjuliapkgstats.com%2Fapi%2Fv1%2Ftotal_downloads%2FComplexityMeasures&query=total_requests&label=Downloads)](http://juliapkgstats.com/pkg/ComplexityMeasures) [![Package Downloads](https://img.shields.io/badge/dynamic/json?url=http%3A%2F%2Fjuliapkgstats.com%2Fapi%2Fv1%2Ftotal_downloads%2FEntropies&query=total_requests&label=Downloads%20(Entropies))](http://juliapkgstats.com/pkg/Entropies) [![publication](https://img.shields.io/badge/publication-arXiv.2406.05011-blueviolet.svg)](https://doi.org/10.48550/arXiv.2406.05011)

ComplexityMeasures.jlは、単変数入力データセットからさまざまな種類の確率、エントロピー、およびその他のいわゆる*複雑性測定*を計算するためのJuliaベースのソフトウェアです。多くの入力データセットにわたる関係測定については、その拡張である[Associations.jl](https://juliadynamics.github.io/Associations.jl/dev/)を参照してください。他のプログラミング言語（Python、R、MATLABなど）のユーザーでも、Juliaの相互運用性によりComplexityMeasures.jlを使用できます。たとえば、Pythonでは[`juliacall`](https://pypi.org/project/juliacall/)を使用します。

広く使用されている代替ソフトウェアとの慎重な比較により、ComplexityMeasures.jlは計算性能、測定の全体量、信頼性、拡張性などのいくつかの客観的な比較の側面で代替品を上回ることが示されています。詳細については関連する出版物を参照してください。

ComplexityMeasures.jlが提供する主な機能は次のように要約できます：

  * データから確率を抽出するための厳密なフレームワークで、[確率空間](https://en.wikipedia.org/wiki/Probability_space)の数学的定式化に基づいています。
  * 複数の（12以上の）結果空間、すなわちデータを確率に離散化する方法。
  * 結果空間が与えられた場合に確率を推定するための複数の推定器で、理論的に知られている推定バイアスを修正します。
  * 非線形ダイナミクス、非線形時系列分析、複雑系の文脈で使用される、さまざまな種類のエントロピー（シャノン、ツァリス、クラダなど）、エクストロピー、およびその他の複雑性測定の情報測定の複数の定義。
  * 理論的に知られている推定バイアスを修正するための、エントロピーのための複数の離散および連続（微分）推定器。
  * 拡張可能なインターフェースと、専用の開発者ドキュメントを伴ったよく考えられたAPI。これにより、新しい結果空間や確率、情報測定、または複雑性測定のための新しい推定器を定義し、ボイラープレートコードなしでソフトウェア内の他のすべてと統合することが簡単になります。

ComplexityMeasures.jlは、スタンドアロンパッケージとして、または[DynamicSystems.jl](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/dynamicalsystems/dev/)や[Associations.jl](https://juliadynamics.github.io/Associations.jl/dev/)などのJuliaDynamics組織の他のプロジェクトの一部として使用できます。

インストールするには、`import Pkg; Pkg.add("ComplexityMeasures")`を実行します。

すべての詳細情報は、[オンライン](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/complexitymeasures/stable/)で見つけるか、`docs/make.jl`ファイルを実行してローカルにビルドすることができます。

*以前は、このパッケージはEntropies.jlと呼ばれていました。*
