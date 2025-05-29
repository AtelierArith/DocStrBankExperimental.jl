# SBMLFBCModels.jl – SBMLフラックスバランス制約モデルのインポートとエクスポート

|                                                                                                                                                                ビルドステータス                                                                                                                                                                 |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| [![CI](https://github.com/COBREXA/SBMLFBCModels.jl/actions/workflows/ci.yml/badge.svg?branch=master)](https://github.com/COBREXA/SBMLFBCModels.jl/actions/workflows/ci.yml) [![codecov](https://codecov.io/gh/COBREXA/SBMLFBCModels.jl/branch/master/graph/badge.svg?token=A2ui7exGIH)](https://codecov.io/gh/COBREXA/SBMLFBCModels.jl) |

パッケージ `SBMLFBCModels.jl` は、SBMLモデル構造（[SBML.jl](https://github.com/LCSB-BioCore/SBML.jl)によって定義される）上に、`AbstractFBCModel`インターフェース（[AbstractFBCModels.jl](https://github.com/COBREXA/AbstractFBCModels.jl)から）を定義します。これにより、制約ベースのモデリングパッケージでSBMLモデルを簡単に使用し、他の制約ベースの代謝モデリングデータ形式に変換することができます。

これの主な目的は、[COBREXA.jl](https://github.com/LCSB-BioCore/COBREXA.jl)および[FBModelTests.jl](https://github.com/LCSB-BioCore/FBCModelTests.jl)のためのSBML読み込み機能を提供することですが、その他は完全に一般的であり、これらのパッケージとは独立して使用できます。

AbstractFBCModelsインターフェースを介してSBMLモデルを読み込むことができるはずです：

```julia
import AbstractFBCModels as M
import SBMLFBCModels

model = M.load("my_model.xml")
```

[AbstractFBCModels.jl](https://github.com/COBREXA/AbstractFBCModels.jl)のドキュメントには、読み込まれたモデルの使用に関する詳細が記載されています。

#### 謝辞

`SBMLFBCModels.jl` は、ルクセンブルク大学のシステム生物医学センター（[uni.lu/lcsb](https://www.uni.lu/lcsb)）およびデュッセルドルフのハインリッヒ・ハイネ大学の定量的および理論的生物学研究所（[qtb.hhu.de](https://www.qtb.hhu.de/en/)）で開発されました。この開発は、欧州連合のホライズン2020プログラムのPerMedCoEプロジェクト（[permedcoe.eu](https://www.permedcoe.eu/)）の下で支援され、契約番号は951773です。

<img src="docs/src/assets/unilu.svg" alt="Uni.lu logo" height="64px">   <img src="docs/src/assets/lcsb.svg" alt="LCSB logo" height="64px">   <img src="docs/src/assets/hhu.svg" alt="HHU logo" height="64px" style="height:64px; width:auto">   <img src="docs/src/assets/qtb.svg" alt="QTB logo" height="64px" style="height:64px; width:auto">   <img src="docs/src/assets/permedcoe.svg" alt="PerMedCoE logo" height="64px">
