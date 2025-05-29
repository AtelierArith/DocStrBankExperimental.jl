# ConceptualClimateModels.jl

[![docsdev](https://img.shields.io/badge/docs-dev-lightblue.svg)](https://juliadynamics.github.io/ConceptualClimateModels.jl/dev/) [![docsstable](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliadynamics.github.io/ConceptualClimateModels.jl/stable/) [![CI](https://github.com/JuliaDynamics/ConceptualClimateModels.jl/workflows/CI/badge.svg)](https://github.com/JuliaDynamics/ConceptualClimateModels.jl/actions?query=workflow%3ACI) [![codecov](https://codecov.io/gh/JuliaDynamics/ConceptualClimateModels.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/JuliaDynamics/ConceptualClimateModels.jl) [![Package Downloads](https://shields.io/endpoint?url=https://pkgs.genieframework.com/api/v1/badge/ConceptualClimateModels)](https://pkgs.genieframework.com?packages=ConceptualClimateModels)

ConceptualClimateModels.jlは、エネルギーバランスモデル、氷河サイクルモデル、気候ティッピングモデルなど、気候の概念モデルを作成および分析するためのJuliaパッケージです。このような概念モデルは、基本的な気候要素の簡略化された表現であり、それらを結びつけるプロセス（エネルギーや質量の流れなど）を含みます。この文脈において、これらのモデルは通常、結合された常微分方程式（部分的または確率的なDEも可能）です。

ConceptualClimateModels.jlは、次の方法でこのようなモデルのモデリングと分析の両方の側面を加速します：

  * *記号表現*から方程式を作成するために[ModelingToolkit.jl](https://docs.sciml.ai/ModelingToolkit/stable/)に基づいています。
  * 気候変数がどのように相互に結びつくか、または気候プロセスが方程式によってどのように表現されるかに関するさまざまな物理的仮説を簡単にテストできる分野特有のフレームワークを提供するために[ProcessBasedModelling.jl](https://github.com/JuliaDynamics/ProcessBasedModelling.jl?tab=readme-ov-file)を利用しています。
  * 現在の文献や進行中の研究からの多くの事前定義されたプロセスを提供します。すべての事前定義されたプロセスは、BiBTeXを使用して文献を厳密に引用します。
  * より多くの気候変数や物理プロセスを追加するのが簡単です。
  * 異なる概念モデルを相互に簡単に結合できます。
  * 既存の気候プロセスに関連するカスタムパラメータの命名を自動化します。
  * [DynamicalSystems.jl](https://juliadynamics.github.io/DynamicalSystemsDocs.jl/dynamicalsystems/dev/)と統合して、典型的な非線形ダイナミクスに基づくワークフローのスタートアップフェーズを自動化します。

今後の機能としては、次のようなものがあります：

  * 緯度モデルのサポート（各変数が緯度円に沿ってベクトル値である場合）
  * 確率的常微分方程式のサポート

インストールするには、`import Pkg; Pkg.add("ConceptualClimateModels")`を実行してください。

さらなる情報は、[オンライン](https://juliadynamics.github.io/ConceptualClimateModels.jl/stable/)で見つけるか、`docs/make.jl`ファイルを実行してローカルにビルドすることができます。

ConceptualClimateModels.jlの開発は、UKRIの工学および物理科学研究評議会の助成金（助成金番号：EP/Y01653X/1、EUマリー・スクリドフスカ・キュリー・ポスドクフェローシップの助成契約）によって資金提供されています。
