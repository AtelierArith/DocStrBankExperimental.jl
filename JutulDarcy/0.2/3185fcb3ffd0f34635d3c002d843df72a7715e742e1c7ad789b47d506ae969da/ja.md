[![Zenodo](https://zenodo.org/badge/477727603.svg)](https://zenodo.org/badge/latestdoi/477727603) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://sintefmath.github.io/JutulDarcy.jl/dev/) [![Build Status](https://github.com/sintefmath/JutulDarcy.jl/actions/workflows/CI.yml/badge.svg?branch=main)](https://github.com/sintefmath/JutulDarcy.jl/actions/workflows/CI.yml?query=branch%3Amain) [![Downloads](https://img.shields.io/badge/dynamic/json?url=http%3A%2F%2Fjuliapkgstats.com%2Fapi%2Fv1%2Fmonthly_downloads%2FJutulDarcy&query=total_requests&suffix=%2Fmonth&label=Downloads&color=green)](https://juliapkgstats.com/pkg/JutulDarcy) [![Downloads](https://img.shields.io/badge/dynamic/json?url=http%3A%2F%2Fjuliapkgstats.com%2Fapi%2Fv1%2Ftotal_downloads%2FJutulDarcy&query=total_requests&&label=Total%20Downloads&color=green)](https://juliapkgstats.com/pkg/JutulDarcy)

[![Jutul Darcy logo](https://github.com/sintefmath/JutulDarcy.jl/raw/main/docs/src/assets/logo_wide.png)](https://sintefmath.github.io/JutulDarcy.jl/dev/)

> [!TIP] Visit the docs at https://sintefmath.github.io/JutulDarcy.jl/dev/


# Juliaによる貯水池シミュレーション

JutulDarcy.jl: Darcyスケールおよび地下水流（CO2貯留、地熱貯水池、ガス/H2貯蔵、石油/ガス田）を使用して、[Jutul.jl](https://github.com/sintefmath/Jutul.jl)を利用して、[SINTEF Digital](https://www.sintef.no/en/digital/)の[応用計算科学グループ](https://www.sintef.no/en/digital/departments-new/applied-mathematics/applied-computational-sciences/)によって開発されました。

## 始めに

[Julia](https://julialang.org/)をインストールし、好みの環境にパッケージを追加します：

```julia
using Pkg
Pkg.add("GLMakie")
Pkg.add("Jutul")
Pkg.add("JutulDarcy")
```

その後、[`examples`](https://github.com/sintefmath/JutulDarcy.jl/tree/main/examples)ディレクトリ内の任意の例をインクルードして実行できます。

業界標準の入力ファイルを実行し、インタラクティブなプロットを生成する最小限の例：

```julia
using JutulDarcy, GLMakie
spe9_dir = JutulDarcy.GeoEnergyIO.test_input_file_path("SPE9")
file_path = joinpath(spe9_dir, "SPE9.DATA")
case = setup_case_from_data_file(file_path)
result = simulate_reservoir(case)
plot_reservoir_simulation_result(case.model, result)
```

インタラクティブなプロットには`GLMakie`が必要であり、SSH経由でJuliaを実行している場合は動作しない可能性があります。

## 主な機能

JutulDarcyは、高性能で汎用的な多孔質メディアシミュレーターで、Juliaで書かれています。力と離散化パラメータに関して完全に微分可能です。

### 物理システム

  * 混合不可能な多相流
  * 溶解した蒸気（Rs）と蒸発した液体（Rv）の両方をサポートする黒油型モデル
  * 最大3相および任意の数の成分を持つ状態方程式組成流
  * 地熱システム

すべてのソルバーは、厳密な質量バランス、摩擦圧力損失、複雑な井戸制限、および時間依存の制御を持つ一般的なマルチセグメント井戸を組み込むことができます。

### アーキテクチャ

  * 純粋なJuliaで書かれ、自動微分と動的スパース性検出を備えています
  * アジョイント法を使用して、任意のモデルパラメータに関する感度をサポート
  * 高性能なアセンブリと線形ソルバー、二段階CPR BILU(0)-CPR Krylovソルバーをサポート
  * ドメイン分解と自動METISパーティショニングを備えたBoomerAMG-CPRソルバーを持つMPIサポート
  * 一貫した離散化（AvgMPFA / NTPFA）をサポート

### 入出力およびワークフローツール

  * コーナーポイントグリッドを持つ.DATAファイルの読み込みと実行をサポートし、非適合の断層と非アクティブセルをサポート。
  * [Matlab Reservoir Simulation Toolbox (MRST)](https://www.mrst.no)からの非構造化グリッドと複雑なケースの入力を`jutul`モジュールを使用して行います
  * [Makie.jl](https://docs.makie.org/stable/)バックエンドを読み込むことで、グリッドと井戸の3Dビジュアライゼーション（Julia 1.9、インタラクティブ用の`GLMakie`が必要）
  * 井戸曲線のインタラクティブプロット

組成シミュレーターは、商業製品であるAD-GPRSおよびMRSTと照合されています。黒油シミュレーターは、標準SPEベンチマーク（SPE1、SPE9など）で検証されています。

## ベンチマークでの例の実行時間

|        名前 |    セル数 | 報告ステップ |             前処理器 | 時間 [s] |
| ---------:| ------:| ------:| ----------------:| ------:|
| SPE1CASE2 |    300 |    120 |     block-ILU(0) |   0.30 |
|      SPE9 |   9000 |     35 |     block-ILU(0) |   3.41 |
|       Egg |  18553 |    123 | CPR-block-ILU(0) |   8.60 |
|     Norne |  44417 |    247 | CPR-block-ILU(0) |  259.0 |
|  OLYMPUS1 | 192750 |     20 | CPR-block-ILU(0) |  162.5 |

CPRを使用したケースでは、AMGソルバーとしてhypreを使用しました。OYMPUS1は、[OLYMPUS最適化ベンチマークチャレンジ](https://link.springer.com/article/10.1007/s10596-020-10003-4)の実現1を指します。数値はシリアルCPUソルブのために提供されています。

## 論文と引用

`JutulDarcy.jl`を説明する主な論文は、*JutulDarcy.jl - 自動微分に基づく完全に微分可能な高性能貯水池シミュレーター*です：

```bibtex
@article{jutuldarcy_ecmor_2024,
   author = "M{\o}yner, O.",
   title = "JutulDarcy.jl - a Fully Differentiable High-Performance Reservoir Simulator Based on Automatic Differentiation", 
   year = "2024",
   volume = "2024",
   number = "1",
   pages = "1-9",
   doi = "https://doi.org/10.3997/2214-4609.202437111",
   publisher = "European Association of Geoscientists \& Engineers",
   issn = "2214-4609",
}
```

[論文はEAGEから入手可能です。](https://doi.org/10.3997/2214-4609.202437111) JutulDarcyを使用する場合は、この論文を引用してください。

## JutulおよびJutulDarcyによって使用されるパッケージのいくつか

Jutulは、Juliaエコシステム内の多くの優れたパッケージに基づいています。以下はそのいくつかと、それらが使用される目的です：

  * [ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl)は、コード全体で使用される双対数クラスを実装しています
  * [SparsityTracing.jl](https://github.com/PALEOtoolkit/SparsityTracing.jl/)は、Jutul内のスパース性検出を提供します
  * [Krylov.jl](https://github.com/JuliaSmoothOptimizers/Krylov.jl)は、反復線形ソルバーを提供します
  * [ILUZero.jl](https://github.com/mcovalt/ILUZero.jl/blob/master/src/ILUZero.jl)はILU(0)前処理器用
  * [AlgebraicMultigrid.jl](https://github.com/JuliaLinearAlgebra/AlgebraicMultigrid.jl)はAMG前処理器用
  * [HYPRE.jl](https://github.com/fredrikekre/HYPRE.jl)はMPIサポートを持つ堅牢なAMG前処理器用
  * [PartitionedArrays.jl](https://github.com/fverdugo/PartitionedArrays.jl)はMPIアセンブリと線形解法用
  * [Tullio.jl](https://github.com/mcabbott/Tullio.jl)は自動最適化ループ用、[Polyester.jl](https://github.com/JuliaSIMD/Polyester.jl)は軽量スレッド用
  * [TimerOutputs.jl](https://github.com/KristofferC/TimerOutputs.jl)と[ProgressMeter.jl](https://github.com/timholy/ProgressMeter.jl)は端末にきれいな出力を提供します。
  * [Makie.jl](https://makie.juliaplots.org/)はビジュアライゼーション機能に使用されます
  * [MultiComponentFlash.jl](https://github.com/moyner/MultiComponentFlash.jl)は多くの組成機能を提供します

...そして、Project.tomlファイル内で直接および間接的に使用される多くの他のパッケージがあります！

# 追加の例とさらなる読み物

[ドキュメント](https://sintefmath.github.io/JutulDarcy.jl/dev/)は主な情報源であり、[例の公開バージョン](https://sintefmath.github.io/JutulDarcy.jl/dev/examples/introduction/wells_intro)も含まれています。さらに、[examples](https://github.com/sintefmath/JutulDarcy.jl/tree/main/examples)フォルダーで詳細情報を確認できます。一部の機能は、[tests](https://github.com/sintefmath/JutulDarcy.jl/tree/main/test)でも示されています。

*内部および文書化されていない関数は、現時点で変更される可能性があります。ただし、例で見られる貯水池シミュレーター自体の主なインターフェースは、かなり安定しているはずです。*
