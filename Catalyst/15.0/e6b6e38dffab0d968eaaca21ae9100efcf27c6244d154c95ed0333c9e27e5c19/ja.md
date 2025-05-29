# Catalyst.jl

[![Latest Release (for users)](https://img.shields.io/badge/docs-latest_release_(for_users)-blue.svg)](https://docs.sciml.ai/Catalyst/stable/) [![API Latest Release (for users)](https://img.shields.io/badge/API-latest_release_(for_users)-blue.svg)](https://docs.sciml.ai/Catalyst/stable/api/) [![Master (for developers)](https://img.shields.io/badge/docs-master_branch_(for_devs)-blue.svg)](https://docs.sciml.ai/Catalyst/dev/) [![API Master (for developers](https://img.shields.io/badge/API-master_branch_(for_devs)-blue.svg)](https://docs.sciml.ai/Catalyst/dev/api/) <!–[![Join the chat at https://julialang.zulipchat.com #sciml-bridged](https://img.shields.io/static/v1?label=Zulip&message=chat&color=9558b2&labelColor=389826)](https://julialang.zulipchat.com/#narrow/stream/279055-sciml-bridged)–>

[![Build Status](https://github.com/SciML/Catalyst.jl/workflows/CI/badge.svg)](https://github.com/SciML/Catalyst.jl/actions?query=workflow%3ACI) [![codecov.io](https://codecov.io/gh/SciML/Catalyst.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/SciML/Catalyst.jl) [![Coverage Status](https://coveralls.io/repos/github/SciML/Catalyst.jl/badge.svg?branch=master)](https://coveralls.io/github/SciML/Catalyst.jl?branch=master)

[![ColPrac: Contributor's Guide on Collaborative Practices for Community Packages](https://img.shields.io/badge/ColPrac-Contributor's%20Guide-blueviolet)](https://github.com/SciML/ColPrac) [![SciML Code Style](https://img.shields.io/static/v1?label=code%20style&message=SciML&color=9558b2&labelColor=389826)](https://github.com/SciML/SciMLStyle) [![Citation](https://img.shields.io/badge/Publication-389826)](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1011530)

Catalyst.jlは、化学反応ネットワークの分析と高性能シミュレーションのためのシンボリックモデリングパッケージです。Catalystは、プログラム的に作成することも、Catalystのドメイン固有言語（DSL）を使用して簡単に指定することができるシンボリック[`ReactionSystem`](https://docs.sciml.ai/Catalyst/stable/catalyst_functionality/programmatic_CRN_construction/)を定義します。[ModelingToolkit.jl](https://github.com/SciML/ModelingToolkit.jl)と[Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl)を活用することで、Catalystは自動ベクトル化と並列処理を通じて大規模なシミュレーションを可能にします。シンボリック`ReactionSystem`は、ModelingToolkitベースのモデルを生成するために使用でき、質量作用ODEモデル、化学ランジュバンSDEモデル、確率的化学動力学ジャンププロセスモデルなどのシミュレーションとパラメータ推定を容易に行うことができます。生成されたモデルは、感度分析、パラメータ推定、機械学習アプリケーションなどのための高レベルのSciMLパッケージを含む、より広範なJuliaおよび[SciML](https://sciml.ai)エコシステム全体でソルバーと共に使用できます。

## インストール

Catalystは以下のようにインストールできます。

```julia
using Pkg

# (オプションですが推奨) Catalystをインストールする新しい環境を作成
Pkg.activate("catalyst_environment")

# 最新のCatalystリリースをインストール
Pkg.add("Catalyst")
```

V15以降、Catalystは特定の依存関係のバージョンを制限しているため、サポートされていない依存関係がすでにインストールされている場合（すなわち、既存の環境にインストールする場合）、古いバージョンのCatalystがインストールされる可能性があります。このため、インストール後は、以下を確認して最新のCatalystバージョンが追加されたことを確認することをお勧めします。

```julia
Pkg.status("Catalyst")
```

## 破壊的変更と新機能

**注意:** バージョン15は破壊的リリースですが、ほとんどの破壊的変更はCatalystの上に開発されているライブラリにのみ影響を与える可能性があります。破壊的変更と新機能の概要については、[HISTORY.md](HISTORY.md)ファイルを参照してください。

## チュートリアルとドキュメント

Catalystの最新のチュートリアルと使用情報は、[安定版ドキュメント](https://docs.sciml.ai/Catalyst/stable/)で入手できます。[開発中のドキュメント](https://docs.sciml.ai/Catalyst/dev/)では、現在のマスターブランチの未リリース機能について説明しています。

パッケージの概要、その機能、および比較ベンチマーキング（バージョン13時点）については、対応する研究論文[Catalyst: Fast and flexible modeling of reaction networks](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1011530)でも見つけることができます。

## 機能

#### Catalystの機能

  * [Catalyst DSL](https://docs.sciml.ai/Catalyst/stable/model_creation/dsl_basics/)は、化学反応表記を使用して反応ネットワークモデルを手動で指定するためのシンプルで読みやすい形式を提供します。
  * Catalyst `ReactionSystem`は、[ModelingToolkit.jl](https://docs.sciml.ai/ModelingToolkit/stable/)と[Symbolics.jl](https://docs.sciml.ai/Symbolics/stable/)に基づいて構築された反応ネットワークのシンボリック表現を提供します。
  * [Catalyst.jl API](http://docs.sciml.ai/Catalyst/stable/api/catalyst_api)は、ネットワークをプログラム的に構築し、複数のネットワークを組み合わせるための機能を提供します。
  * ModelingToolkitを活用することで、生成されたモデルはシンボリック反応速度方程式ODEモデル、シンボリック化学ランジュバン方程式モデル、シンボリック確率的化学動力学（ジャンププロセス）モデルに変換できます。これらは任意の[DifferentialEquations.jl](https://docs.sciml.ai/DiffEqDocs/stable/) [ODE/SDE/ジャンプソルバー](https://docs.sciml.ai/Catalyst/stable/model_simulation/simulation_introduction/)を使用してシミュレーションでき、[並列化されたパラメータスイープと統計的サンプリング](https://docs.sciml.ai/Catalyst/stable/model_simulation/ensemble_simulations/)を実行するための`EnsembleProblem`内で使用できます。すべての解の[可視化](https://docs.sciml.ai/Catalyst/stable/model_simulation/simulation_plotting/)のためのプロットレシピが利用可能です。
  * 非整数（例：`Float64`）の化学量論係数[がサポートされています](https://docs.sciml.ai/Catalyst/stable/model_creation/dsl_basics/#dsl_description_stoichiometries_decimal)ODEモデルを生成するために、すべてのシステムタイプに対して化学量論係数の[シンボリック表現がサポートされています](https://docs.sciml.ai/Catalyst/stable/model_creation/parametric_stoichiometry/)。
  * [ネットワーク分析スイート](https://docs.sciml.ai/Catalyst/stable/model_creation/network_analysis/)は、連結クラス、欠陥、可逆性、その他のネットワーク特性の計算を許可します。
  * [保存則を検出して利用することができます](https://docs.sciml.ai/Catalyst/stable/model_creation/conservation_laws/)システムサイズを削減し、ODE、SDE、定常状態方程式への変換中に非特異的ヤコビ行列を生成します。
  * Catalyst反応ネットワークモデルは、[微分方程式と代数方程式と結合することができます](https://docs.sciml.ai/Catalyst/stable/model_creation/constraint_equations/)（これらはODE、SDE、定常状態方程式への変換中に組み込まれます）。
  * モデルは、シミュレーション中にシステムとその状態に影響を与える[イベントと結合することができます](https://docs.sciml.ai/Catalyst/stable/model_creation/constraint_equations/#constraint_equations_events)。
  * ModelingToolkitを活用することで、ユーザーはソルバーで使用するための最適化されたシステム表現を生成するためのさまざまなオプションを持っています。これには、[密なまたは疎なヤコビ行列の構築](https://docs.sciml.ai/Catalyst/stable/model_simulation/ode_simulation_performance/#ode_simulation_performance_sparse_jacobian)、[生成された導関数関数のマルチスレッドまたは並列化](https://docs.sciml.ai/Catalyst/stable/model_simulation/ode_simulation_performance/#ode_simulation_performance_parallelisation)、[Gillespie型シミュレーションのための最適化されたジャンプタイプへの反応の自動分類](https://docs.sciml.ai/JumpProcesses/stable/jump_types/#jump_types)、[ジャンプシステムのための依存関係グラフの自動構築](https://docs.sciml.ai/JumpProcesses/stable/jump_types/#Jump-Aggregators-Requiring-Dependency-Graphs)などが含まれます。
  * [Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl)のシンボリック表現とJuliaの`Expr`は、生成されたODE、SDE、またはジャンプモデル内の決定論的および確率的項を決定するすべての速度法則と関数に対して取得できます。
  * [定常状態](https://docs.sciml.ai/Catalyst/stable/steady_state_functionality/homotopy_continuation/)（およびその[安定性](https://docs.sciml.ai/Catalyst/stable/steady_state_functionality/steady_state_stability_computation/)）は、モデルODE表現のために計算できます。

#### Catalystが他のパッケージと組み合わせる機能

  * [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl)は、生成された反応速度方程式ODEモデルを数値的に解くために使用できます。
  * [StochasticDiffEq.jl](https://github.com/SciML/StochasticDiffEq.jl)は、生成された化学ランジュバン方程式SDEモデルを数値的に解くために使用できます。
  * [JumpProcesses.jl](https://github.com/SciML/JumpProcesses.jl)は、生成された確率的化学動力学ジャンププロセスモデルを数値的にサンプリングするために使用できます。
  * [すべてのシミュレーションの並列化](https://docs.sciml.ai/Catalyst/stable/model_simulation/ode_simulation_performance/#ode_simulation_performance_parallelisation)のサポート、[ODE](https://docs.sciml.ai/Catalyst/stable/model_simulation/ode_simulation_performance/#ode_simulation_performance_parallelisation_GPU)および[SDE](https://docs.sciml.ai/Catalyst/stable/model_simulation/sde_simulation_performance/#sde_simulation_performance_parallelisation_GPU)シミュレーションのGPU上での並列化を含む、[DiffEqGPU.jl](https://github.com/SciML/DiffEqGPU.jl)を使用しています。
  * [Latexify](https://korsbo.github.io/Latexify.jl/stable/)は、生成された数学モデルまたは基礎となる反応のセットに対応する[LaTeX表現を生成するために使用できます](https://docs.sciml.ai/Catalyst/stable/model_creation/model_visualisation/#visualisation_latex)。
  * [GraphMakie](https://github.com/MakieOrg/GraphMakie.jl)は、反応ネットワークグラフを生成し、[可視化するために使用できます](https://docs.sciml.ai/Catalyst/stable/model_creation/model_visualisation/#visualisation_graphs)。
  * モデルの定常状態は、[HomotopyContinuation.jl](https://github.com/JuliaHomotopyContinuation/HomotopyContinuation.jl)を使用して[ホモトピー継続](https://docs.sciml.ai/Catalyst/stable/steady_state_functionality/homotopy_continuation/)を通じて計算できます（これにより、複数の定常状態を持つシステムの*すべて*の定常状態を見つけることができます）、[SteadyStateDiffEq.jl](https://github.com/SciML/SteadyStateDiffEq.jl)を使用した[前方ODEシミュレーション](https://docs.sciml.ai/Catalyst/stable/steady_state_functionality/nonlinear_solve/#steady_state_solving_simulation)、または[NonlinearSolve.jl](https://github.com/SciML/NonlinearSolve.jl)を使用して[定常状態の非線形方程式を数値的に解く](https://docs.sciml.ai/Catalyst/stable/steady_state_functionality/nonlinear_solve/#steady_state_solving_nonlinear)ことができます。
  * [BifurcationKit.jl](https://github.com/bifurcationkit/BifurcationKit.jl)は、モデルの定常状態の[分岐図を計算するために使用できます](https://docs.sciml.ai/Catalyst/stable/steady_state_functionality/bifurcation_diagrams/)（周期的軌道を見つけることを含む）。
  * [DynamicalSystems.jl](https://github.com/JuliaDynamics/DynamicalSystems.jl)は、モデルの[吸引盆地](https://docs.sciml.ai/Catalyst/stable/steady_state_functionality/dynamical_systems/#dynamical_systems_basins_of_attraction)、[リャプノフスペクトル](https://docs.sciml.ai/Catalyst/stable/steady_state_functionality/dynamical_systems/#dynamical_systems_lyapunov_exponents)、およびその他の動的システム特性を計算するために使用できます。
  * [Optimization.jl](https://github.com/SciML/Optimization.jl)と[PEtab.jl](https://github.com/sebapersson/PEtab.jl)は、[モデルパラメータをデータにフィットさせるために使用できます](https://sebapersson.github.io/PEtab.jl/stable/Define_in_julia/)。
  * [GlobalSensitivity.jl](https://github.com/SciML/GlobalSensitivity.jl)は、モデルの振る舞いの[グローバル感度分析を実行するために使用できます](https://docs.sciml.ai/Catalyst/stable/inverse_problems/global_sensitivity_analysis/)。
  * [SciMLSensitivity.jl](https://github.com/SciML/SciMLSensitivity.jl)は、前方モデルシミュレーションを含む関数の局所感度を計算するために使用できます。
  * [StructuralIdentifiability.jl](https://github.com/SciML/StructuralIdentifiability.jl)は、[構造同定可能性分析を実行するために使用できます](https://docs.sciml.ai/Catalyst/stable/inverse_problems/structural_identifiability/)。

#### Catalystに基づいて構築されたパッケージの機能

  * Catalyst [`ReactionSystem`](@ref)sは、[SBMLファイルからインポートすることができます](https://docs.sciml.ai/Catalyst/stable/model_creation/model_file_loading_and_export/#Loading-SBML-files-using-SBMLImporter.jl-and-SBMLToolkit.jl) [SBMLImporter.jl](https://github.com/sebapersson/SBMLImporter.jl)と[SBMLToolkit.jl](https://github.com/SciML/SBMLToolkit.jl)を介して、[BioNetGen .netファイルから](https://docs.sciml.ai/Catalyst/stable/model_creation/model_file_loading_and_export/#file_loading_rni_net)およびさまざまな化学量論行列ネットワーク表現を使用して[ReactionNetworkImporters.jl](https://github.com/SciML/ReactionNetworkImporters.jl)を介してインポートできます。
  * [MomentClosure.jl](https://github.com/augustinas1/MomentClosure.jl)は、Catalystで定義された反応ネットワークから化学マスター方程式のモーメント閉じ込め近似を表すシンボリックModelingToolkit `ODESystem`を生成することを可能にします。
  * [FiniteStateProjection.jl](https://github.com/kaandocal/FiniteStateProjection.jl)は、Catalystで定義された反応ネットワークから化学マスター方程式モデルを構築し、数値的に解くことを可能にします。
  * [DelaySSAToolkit.jl](https://github.com/palmtree2013/DelaySSAToolkit.jl)は、Catalyst反応ネットワークモデルに遅延を追加し、遅延モデルを持つ確率的化学動力学をシミュレートすることができます。

## 例示的な例

#### ミカエリス・メンテン酵素動力学の決定論的ODEシミュレーション

ここでは、Catalyst DSLを使用してモデルを作成し、通常の微分方程式としてシミュレーションする簡単な例を示します。

```julia
# 必要なパッケージを取得します。
using Catalyst, OrdinaryDiffEqDefault, Plots

# モデルを作成します。
model = @reaction_network begin
    kB, S + E --> SE
    kD, SE --> S + E
    kP, SE --> P + E
end

# シミュレーション可能なODEを作成します。
u0 = [:S => 50.0, :E => 10.0, :SE => 0.0, :P => 0.0]
tspan = (0., 200.)
ps = [:kB => 0.01, :kD => 0.1, :kP => 0.1]
ode = ODEProblem(model, u0, tspan, ps)

# ODEをシミュレーションし、結果をプロットします。
sol = solve(ode)
plot(sol; lw = 5)
```

![ODEシミュレーション](docs/src/assets/readme_ode_plot.svg)

#### 確率的ジャンプシミュレーション

同じモデルを他のタイプのシミュレーションの入力として使用できます。例えば、ここでは反応ネットワークのために確率的化学動力学ジャンププロセスモデルを生成してシミュレーションします。ジャンププロセスの正確な実現が自動選択された確率的シミュレーションアルゴリズム（SSA）を使用してサンプリングされます（現在の例の小さなネットワークでは、ギレスピーの直接法になります）：

```julia
# 初期条件は、各種の正確な個体数を追跡するために整数になります。
using JumpProcesses
u0_integers = [:S => 50, :E => 10, :SE => 0, :P => 0]
jinput = JumpInputs(model, u0_integers, tspan, ps)
jprob = JumpProblem(jinput)
jump_sol = solve(jprob)
plot(jump_sol; lw = 2)
```

![ジャンプシミュレーション](docs/src/assets/readme_jump_plot.svg)

## より詳細な例

上記の例では、基本的なCatalystワークフローを使用してシンプルなモデルをシミュレーションしました。ここでは、さまざまなCatalyst機能が組み合わさって、はるかに高度なモデルを作成する方法を示します。私たちのモデルは、細胞の体積（$V$）が成長因子（$G$）によってどのように影響を受けるかを説明します。成長因子は、リン酸化された形（$G^P$）のときのみ成長を促進します。$G$のリン酸化（$G \to G^P$）は、太陽光によって促進され、これは周期的な正弦波$k_a (\sin(t) + 1)$としてモデル化されます。細胞が臨界体積（$V_m$）に達すると、細胞分裂が起こります。まず、モデルを宣言します。

```julia
using Catalyst
cell_model = @reaction_network begin
    @parameters Vₘ g
    @equations begin
        D(V) ~ g*Gᴾ
    end
    @continuous_events begin
        [V ~ Vₘ] => [V ~ V/2]
    end
    kₚ*(sin(t)+1)/V, G --> Gᴾ
    kᵢ/V, Gᴾ --> G
end
```

次に、化学ランジュバンダイナミクスSDEモデルとしてシステムを研究します。これは以下のように生成できます。

```julia
u0 = [:V => 25.0, :G => 50.0, :Gᴾ => 0.0]
tspan = (0.0, 20.0)
ps = [:Vₘ => 50.0, :g => 0.3, :kₚ => 100.0, :kᵢ => 60.0]
sprob = SDEProblem(cell_model, u0, tspan, ps)
```

この問題は、次の確率微分方程式モデルをエンコードします：

$$
\begin{align*}
dG(t) &=  - \left( \frac{k_p(\sin(t)+1)}{V(t)} G(t) + \frac{k_i}{V(t)} G^P(t) \right) dt - \sqrt{\frac{k_p (\sin(t)+1)}{V(t)} G(t)} \, dW_1(t) + \sqrt{\frac{k_i}{V(t)} G^P(t)} \, dW_2(t) \\
dG^P(t) &= \left( \frac{k_p(\sin(t)+1)}{V(t)} G(t) - \frac{k_i}{V(t)} G^P(t) \right) dt + \sqrt{\frac{k_p (\sin(t)+1)}{V(t)} G(t)} \, dW_1(t) - \sqrt{\frac{k_i}{V(t)} G^P(t)} \, dW_2(t) \\
dV(t) &= \left(g \, G^P(t)\right) dt
\end{align*}
$$

ここで、$dW_1(t)$および$dW_2(t)$の項は独立したブラウン運動を表し、化学ランジュバン方程式によって追加されたノイズをエンコードします。最後に、シミュレーションを行い、結果をプロットします。

```julia
using StochasticDiffEq, Plots
sol = solve(sprob, EM(); dt = 0.05)
plot(sol; xguide = "Time (au)", lw = 2)
```

![詳細なSDEシミュレーション](docs/src/assets/readme_elaborate_sde_plot.svg)

ここで使用した機能のいくつか：

  * 細胞の体積は[微分方程式としてモデル化され、反応ネットワークモデルに結合されました](https://docs.sciml.ai/Catalyst/stable/model_creation/constraint_equations/#constraint_equations_coupling_constraints)。
  * 細胞分裂は、[モデルにイベントを組み込むことによって作成されました](https://docs.sciml.ai/Catalyst/stable/model_creation/constraint_equations/#constraint_equations_events)。
  * 特定の数値[ソルバーと対応するソルバーオプションを指定しました](https://docs.sciml.ai/Catalyst/stable/model_simulation/simulation_introduction/#simulation_intro_solver_options)。
  * モデルシミュレーションは[Plots.jlを使用してプロットされました](https://docs.sciml.ai/Catalyst/stable/model_simulation/simulation_plotting/)。

## ヘルプを得るか、参加する方法

Catalystの開発者は、[Julia Discourse](https://discourse.julialang.org/)および[Julia Slack](https://julialang.slack.com)の#sciml-bridgedおよび#sciml-sysbioチャンネルで活動しています。バグや機能リクエストについては、[問題をオープンしてください](https://github.com/SciML/Catalyst.jl/issues)。

## Catalyst.jlをサポートし、引用する

このエコシステム内のソフトウェアは、学術研究の一環として開発されました。サポートしていただける場合は、リポジトリにスターを付けていただけると幸いです。これらのメトリクスは、将来的に資金を確保するのに役立つかもしれません。研究、教育、またはその他の活動の一環としてCatalystを使用する場合は、私たちの研究を引用していただけると感謝いたします：

```
@article{CatalystPLOSCompBio2023,
 doi = {10.1371/journal.pcbi.1011530},
 author = {Loman, Torkel E. AND Ma, Yingbo AND Ilin, Vasily AND Gowda, Shashi AND Korsbo, Niklas AND Yewale, Nikhil AND Rackauckas, Chris AND Isaacson, Samuel A.},
 journal = {PLOS Computational Biology},
 publisher = {Public Library of Science},
 title = {Catalyst: Fast and flexible modeling of reaction networks},
 year = {2023},
 month = {10},
 volume = {19},
 url = {https://doi.org/10.1371/journal.pcbi.1011530},
 pages = {1-19},
 number = {10},
}
```
