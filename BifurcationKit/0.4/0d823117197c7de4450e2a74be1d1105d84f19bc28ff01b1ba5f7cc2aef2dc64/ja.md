```julia
struct PoincareShootingProblem{Tf, Tjac<:BifurcationKit.AbstractJacobianType, Tsection<:BifurcationKit.SectionPS, Tpar, Tlens} <: BifurcationKit.AbstractPoincareShootingProblem
```

この複合型は、ポアンカレ帰納法を使用して周期軌道を特定するためのポアンカレ射撃法を実装しています。詳細（数学、表記、線形システム）については、[こちら](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/periodicOrbitShooting/)を参照してください。引数は以下のように説明されています。

# フィールド

  * `M::Int64`: `M`: ポアンカレセクションの数。`M == 1` の場合は単純な射撃が実装され、それ以外の場合は複数の射撃が実装されます。デフォルト: 0
  * `flow::Any`: `flow::Flow`: 構造体 [`Flow`](@ref) を通じてコーシー問題の流れを実装します。デフォルト: Flow()
  * `section::BifurcationKit.SectionPS`: `sections`: ポアンカレセクション条件を実装する関数または呼び出し可能な構造体。評価 `sections(x)` は、`M == 1` の場合にスカラー数を返す必要があります。それ以外の場合は、`section(out, x)` 関数を実装して `out` に `M` セクションを格納する必要があります。ハイパープレーンとして定義されたセクションの型については [`SectionPS`](@ref) を参照してください。デフォルト: SectionPS(M)
  * `δ::Float64`: `δ = 1e-8` は有限差分によって関数のヤコビアンを計算するために使用されます。`0` に設定すると、ヤコビアンの解析的表現が代わりに使用されます。デフォルト: 0.0
  * `parallel::Bool`: `parallel = false` 射撃が並列（スレッド）で計算されるかどうか。`EnsembleProblem` によって定義されたフローを使用することでのみ利用可能です。デフォルト: false
  * `par::Any`: `par` モデルのパラメータ デフォルト: 何も指定されていない
  * `lens::Any`: `lens` パラメータ軸 デフォルト: 何も指定されていない
  * `update_section_every_step::UInt64`: `update_section_every_step` 継続中に `update_section_every_step` ステップごとにセクションを更新します デフォルト: 1
  * `jacobian::BifurcationKit.AbstractJacobianType`: ニュートン反復で使用されるヤコビアンの型を説明します（以下を参照）。デフォルト: AutoDiffDenseAnalytical()

## ヤコビアン

  * `jacobian` 線形アルゴリズムの選択を指定します。これは `[AutoDiffMF(), MatrixFree(), AutodiffDense(), AutoDiffDenseAnalytical(), FiniteDifferences(), FiniteDifferencesMF()]` に属する必要があります。これはヤコビアン dG を反転する方法を選択するために使用されます。

      * `MatrixFree()` の場合、行列フリーのヤコビアンで、ヤコビアンはユーザーによって `prob` に指定されます。これは線形システムを解決するために反復ソルバー（例: GMRES）と一緒に使用されます。
      * `AutoDiffMF()` の場合、方向微分を使用して `x -> prob(x, p)` の（行列フリーの）導関数を計算するために自動微分（AD）を使用します。これは線形システムを解決するために反復ソルバー（例: GMRES）と一緒に使用されます。
      * `AutodiffDense()` の場合。`AutoDiffMF` と同様ですが、ヤコビアンは密な行列として形成されます。直接ソルバーまたは反復ソルバーを使用できます。
      * `FiniteDifferences()` の場合、`AutoDiffDense` と同様ですが、`δ = 1e-8` を使用して `x -> prob(x, p)` のヤコビアンを計算するために有限差分を使用します。これは引数として渡すことができます。
      * `AutoDiffDenseAnalytical()` の場合。`AutoDiffDense` と同様ですが、ヤコビアンはADと解析的な式の混合を使用して形成されます。
      * `FiniteDifferencesMF()` の場合、`δ = 1e-8` を使用して `x -> prob(x, p)` の行列フリーのヤコビアンを計算するために有限差分を使用します。これは引数として渡すことができます。

## 簡略化されたコンストラクタ

  * 最初の重要なコンストラクタは、ホップ分岐点から周期軌道に分岐するために使用される以下のものです。 `pb = PoincareShootingProblem(M::Int, prob::Union{ODEProblem, EnsembleProblem}, alg; kwargs...)`
  * 機能を作成する便利な方法は次のとおりです。

`pb = PoincareShootingProblem(prob::ODEProblem, alg, section; kwargs...)`

単純な射撃用または

`pb = PoincareShootingProblem(prob::Union{ODEProblem, EnsembleProblem}, alg, M::Int, section; kwargs...)`

複数の射撃用です。ここで `prob` は、ODEソルバー `alg`（例えば `Tsit5()`）を使用してフローを作成するために使用される `Union{ODEProblem, EnsembleProblem}` です。最後に、引数 `kwargs` はフローを定義するODEソルバーに渡されます。詳細については `DifferentialEquations.jl` を参照してください。

  * 別の便利な呼び出しは次のとおりです。

`pb = PoincareShootingProblem(prob::Union{ODEProblem, EnsembleProblem}, alg, normals::AbstractVector, centers::AbstractVector; δ = 1e-8, kwargs...)`

ここで `normals`（および `centers`）は、ハイパープレーン $\Sigma_i$ のリストを定義する法線（および中心）のリストです。これらのハイパープレーンは部分的なポアンカレ帰納法を定義するために使用されます。

## 機能の計算

機能は、ここで `G` と呼ばれる射撃問題をエンコードします。次に、`pb(orbitguess, par)` を呼び出して、推測に機能を適用できます。`orbitguess::AbstractVector` はサイズ M * N である必要があり、ここで N は状態空間の未知数の数で、`M` はポアンカレマップの数です。もう一つ受け入れられる `guess` は、`guess[i]` が `i` 番目のセクションの軌道の状態であるというものです。この最後の形式は、2次元問題などに便利な非ベクトル状態空間を可能にします。

この推測は、`generate_solution` を使用して関数解から生成できます。

  * `pb(orbitguess, par)` は `orbitguess` に対して機能 G を評価します。
  * `pb(orbitguess, par, du)` は `du` に対して `orbitguess` での機能のヤコビアン `dG(orbitguess).du` を評価します。
  * `pb(Val(:JacobianMatrixInplace), J, x, par)` は、解析的に機能のヤコビアンを計算します。これは ForwardDiff.jl に基づいています。主にODEに対して便利です。
  * `pb(Val(:JacobianMatrix), x, par)` は、上記と同様ですが、アウトオブプレースです。

!!! tip
    `getperiod(pb, sol, par)` 関数を使用して、パラメータ `par` の問題に対する解 `sol` の周期を取得できます。

