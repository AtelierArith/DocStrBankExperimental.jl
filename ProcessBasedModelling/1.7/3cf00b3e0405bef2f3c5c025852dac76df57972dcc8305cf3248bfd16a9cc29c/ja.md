# ProcessBasedModelling.jl

[![docsdev](https://img.shields.io/badge/docs-dev-lightblue.svg)](https://juliadynamics.github.io/ProcessBasedModelling.jl/dev/) [![docsstable](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliadynamics.github.io/ProcessBasedModelling.jl/stable/) [![CI](https://github.com/JuliaDynamics/ProcessBasedModelling.jl/workflows/CI/badge.svg)](https://github.com/JuliaDynamics/ProcessBasedModelling.jl/actions?query=workflow%3ACI) [![codecov](https://codecov.io/gh/JuliaDynamics/ProcessBasedModelling.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/JuliaDynamics/ProcessBasedModelling.jl) [![Package Downloads](https://shields.io/endpoint?url=https://pkgs.genieframework.com/api/v1/badge/ProcessBasedModelling)](https://pkgs.genieframework.com?packages=ProcessBasedModelling)

ProcessBasedModelling.jlは、記号式表現を使用して方程式のモデルを構築するための[ModelingToolkit.jl](https://docs.sciml.ai/ModelingToolkit/stable/)（MTK）への拡張です。これは、MTKの[ネイティブコンポーネントベースのモデリング](https://docs.sciml.ai/ModelingToolkit/stable/tutorials/acausal_components/)の代替フレームワークですが、コンポーネントの代わりに「プロセス」があります。このアプローチは、各変数が特定の物理的概念または観測可能なものに対応し、MTKの「ファクトリー」の定義を価値あるものにするための重複変数がほとんど（または全く）ない物理的/生物学的/その他のシステムのモデリングに役立ちます。一方で、与えられた物理的概念を方程式形式で表現するためのさまざまな物理的表現、または*プロセス*がたくさんあります。多くの科学分野では、このアプローチは「コンポーネント」アプローチよりも研究者のモデリングの推論により密接に平行しています。

この推論スタイルを超えて、ProcessBasedModelling.jlの最大の強みは、**不正確/不完全な方程式に関する情報豊富なエラーと自動化**です。ProcessBasedModelling.jlを介してMTKモデルを構築する際、ユーザーは「プロセス」のベクトルを提供します：定義が明確で単一の左辺変数を持つ方程式またはカスタムタイプです。これにより、ProcessBasedModelling.jlは以下を行うことができます：

1. プロセスを反復処理し、提供されたプロセスによって導入されたが、プロセスが割り当てられていない*新しい*変数を収集します。
2. これらの収集された「プロセスなし」変数について：

      * デフォルトプロセスが定義されている場合、これをモデルに組み込みます。
      * デフォルトプロセスがないが、変数にデフォルト値がある場合、その変数を同じデフォルト値を持つ*パラメータ*に等しくし、情報豊富な警告を投げます。
      * それ以外の場合、元々提供された変数がこの新しい「プロセスなし」変数を導入したことを正確に示す情報豊富なエラーを投げます。
3. 変数に2つのプロセスが誤って割り当てられている場合、情報豊富なエラーを投げます。

私たちの経験では、またオンラインドキュメントでも明示的に強調しているように、このアプローチは通常、ネイティブMTKのものよりもシンプルであいまいさの少ない、よりターゲットを絞った警告やエラーメッセージを生成します。これにより、構成された方程式の問題の特定と解決が迅速に行えます。

ProcessBasedModelling.jlは、物理的/生物学的/その他のシステムに関するモデルを開発し、特定の物理的観測可能なものに対してさまざまな物理的「ルール」（結合、フィードバック、メカニズムなど）を効率的に試すのに特に適しています。これは、同じ変数に対応する異なるプロセス間を恣意的に切り替えることを意味します。したがって、ProcessBasedModelling.jlのターゲットアプリケーションは、文脈固有の事前定義されたコンポーネントの存在に依存せず、事前定義されたプロセスを提供する分野特有のライブラリを開発するためのフレームワークです。使用例は[ConceptualClimateModels.jl](https://github.com/JuliaDynamics/ConceptualClimateModels.jl)にあります。

情報豊富なエラーに加えて、ProcessBasedModelling.jlはまた

1. フィールド特有のライブラリの開発を加速するために、いくつかの一般的なプロセスのサブタイプをすぐに提供します。
2. デフォルトで提供されるプロセスによって導入されたパラメータに対応する名前付きMTK変数とパラメータを自動的に作成します。これにより、明示的にコーディングされることなく直感的な名前が得られ、オプトアウトも可能です。
3. フィールド特有のライブラリをさらに構築するためのユーティリティ関数を提供します。

このパッケージの使用方法やその有用性を強調する例については、オンラインのドキュメントを参照してください。

ProcessBasedModelling.jlの開発は、UKRIの工学および物理科学研究評議会によって資金提供されており、助成金番号はEP/Y01653X/1（ジョージ・ダツェリスのEUマリー・スコロドフスカ＝キュリー・ポスドクフェローシップのための助成契約）です。
