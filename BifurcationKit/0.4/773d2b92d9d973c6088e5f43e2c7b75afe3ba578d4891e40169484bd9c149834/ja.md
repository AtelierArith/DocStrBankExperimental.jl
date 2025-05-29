```julia
struct ShootingProblem{Tf<:BifurcationKit.AbstractFlow, Tjac<:BifurcationKit.AbstractJacobianType, Ts, Tsection, Tpar, Tlens} <: BifurcationKit.AbstractShootingProblem
```

周期軌道を見つけるために、単純/並列の複数標準射撃法を実装する問題を作成します。詳細（数学、表記、線形システム）は[こちら](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/periodicOrbitShooting/)で確認できます。引数は以下のように説明されています。

射撃問題をエンコードする関数を `G` と呼びます。例えば、以下のメソッドが利用可能です：

  * `pb(orbitguess, par)` は `orbitguess` に対して関数 G を評価します。
  * `pb(orbitguess, par, du)` は `du` に対して `orbitguess` でのヤコビアン `dG(orbitguess)⋅du` 関数を評価します。
  * `pb(Val(:JacobianMatrixInplace), J, x, par)` は関数のヤコビアンを解析的に計算します。これは ForwardDiff.jl に基づいています。主に ODE に便利です。
  * `pb(Val(:JacobianMatrix), x, par)` は上記と同じですが、アウトオブプレースです。

その後、`pb(orbitguess, par)` を呼び出して、推測に関数を適用できます。`orbitguess::AbstractVector` はサイズ `M * N + 1` でなければならず、ここで N は状態空間の未知数の数であり、`orbitguess[M * N + 1]` はリミットサイクルの周期 `T` の推定値です。この推測の形式は、`IterativeSolvers.jl` などの線形ソルバーの使用に便利です（例えば、`AbstractVector` のみを受け入れます）。もう一つの受け入れられる推測は、`BorderedArray(guess, T)` の形式であり、ここで `guess[i]` は `i` 番目の時間スライスでの軌道の状態です。この最後の形式は、2次元の問題に便利な非ベクトル状態空間を許可します。この場合、線形ソルバーには `GMRESKrylovKit` を使用します。

この推測は、`generate_solution` または `generate_ci_problem` を使用して関数解から生成できます。

# フィールド

  * `M::Int64`: `ds`: 各射撃の時間差のベクトル。長さは `M` で表されます。`M == 1` の場合、単純な射撃が実装され、それ以外の場合は複数の射撃が実装されます。デフォルト: 0
  * `flow::BifurcationKit.AbstractFlow`: `flow::Flow`: 構造 [`Flow`](@ref) を通じて Cauchy 問題の流れを実装します。デフォルト: Flow()
  * `ds::Any`: デフォルト: diff(LinRange(0, 1, M + 1))
  * `section::Any`: `section`: 位相条件を実装します。評価 `section(x, T)` はスカラー数を返さなければならず、ここで `x` は周期軌道の **1点** に対する推測であり、`T` は推測の周期です。また、メソッド `section(x, T, dx, dT)` が利用可能であり、`section` の微分を返さなければなりません。`x` の型はニュートンソルバーに渡されるものによって異なります。ハイパープレーンとして定義されたセクションの型については [`SectionSS`](@ref) を参照してください。デフォルト: 何も指定されていません
  * `parallel::Bool`: `parallel` は射撃が並列（スレッド）で計算されるかどうかを示します。これは `EnsembleProblem` によって定義されたフローを使用することで利用可能です（これは自動的に設定されます）。デフォルト: false
  * `par::Any`: `par` モデルのパラメータ デフォルト: 何も指定されていません
  * `lens::Any`: `lens` パラメータ軸。デフォルト: 何も指定されていません
  * `update_section_every_step::UInt64`: 継続中に `update_section_every_step` ステップごとにセクションを更新します デフォルト: 1
  * `jacobian::BifurcationKit.AbstractJacobianType`: ニュートン反復で使用されるヤコビアンの型を説明します（以下を参照）。デフォルト: AutoDiffDense()

## ヤコビアン

  * `jacobian` 線形アルゴリズムの選択を指定します。これは `[AutoDiffMF(), MatrixFree(), AutodiffDense(), AutoDiffDenseAnalytical(), FiniteDifferences(), FiniteDifferencesMF()]` に属する必要があります。これはヤコビアン dG の逆行列を選択するために使用されます。

      * `MatrixFree()` の場合、ユーザーが `prob` で指定したヤコビアンは行列フリーです。これは線形システムを解くために反復ソルバー（例：GMRES）と一緒に使用されます。
      * `AutoDiffMF()` の場合、方向微分を使用して `x -> prob(x, p)` の（行列フリー）導関数を計算するために自動微分（AD）を使用します。これは線形システムを解くために反復ソルバー（例：GMRES）と一緒に使用されます。
      * `AutodiffDense()` の場合。`AutoDiffMF` と同様ですが、ヤコビアンは密な行列として形成されます。直接ソルバーまたは反復ソルバーを使用できます。
      * `FiniteDifferences()` の場合、`AutoDiffDense` と同様ですが、`δ = 1e-8` を使用して `x -> prob(x, p)` のヤコビアンを計算します。これは引数として渡すことができます。
      * `AutoDiffDenseAnalytical()` の場合。`AutoDiffDense` と同様ですが、ヤコビアンは AD と解析的な式の混合を使用して形成されます。
      * `FiniteDifferencesMF()` の場合、`δ = 1e-8` を使用して `x -> prob(x, p)` の行列フリーのヤコビアンを計算します。これは引数として渡すことができます。

## 簡略化されたコンストラクタ

  * 最初の重要なコンストラクタは、ホップ分岐点から周期軌道に分岐するために使用される以下のものです：

```
pb = ShootingProblem(M::Int, prob::Union{ODEProblem, EnsembleProblem}, alg; kwargs...)
```

  * 関数を構築する便利な方法は、次のように使用することです：

```
pb = ShootingProblem(prob::Union{ODEProblem, EnsembleProblem}, alg, centers::AbstractVector; kwargs...)
```

ここで `prob` は ODEProblem（または EnsembleProblem）であり、ODE ソルバー `alg`（例えば `Tsit5()`）を使用してフローを作成するために使用されます。`centers` は周期軌道に近い `M` 点のリストであり、位相の制約を構築するために使用されます。`parallel = false` は、複数の射撃の場合に複数の軌道をシミュレートするために並列シミュレーション（スレッド）を使用するオプションです。これは、軌道の計算が比較的長い場合に効率的です。最後に、引数 `kwargs` はフローを定義する ODE ソルバーに渡されます。詳細については `DifferentialEquations.jl` を参照してください。この場合、フローの導関数は内部で有限差分を使用して計算されます。

  * より多くのオプションを持つ射撃問題を作成する別の方法は、特に位相のために独自のスカラー制約 `section(x)::Number` を提供できる以下のものです：

```
pb = ShootingProblem(prob::Union{ODEProblem, EnsembleProblem}, alg, M::Int, section; parallel = false, kwargs...)
```

または

```
pb = ShootingProblem(prob::Union{ODEProblem, EnsembleProblem}, alg, ds, section; parallel = false, kwargs...)
```

  * 次の方法は、前のものの発展です

```
pb = ShootingProblem(prob1::Union{ODEProblem, EnsembleProblem}, alg1, prob2::Union{ODEProblem, EnsembleProblem}, alg2, M::Int, section; parallel = false, kwargs...)
```

または

```
pb = ShootingProblem(prob1::Union{ODEProblem, EnsembleProblem}, alg1, prob2::Union{ODEProblem, EnsembleProblem}, alg2, ds, section; parallel = false, kwargs...)
```

ここで、2つの `ODEProblem` を提供します。最初の `prob1` は `F` に関連するフローを定義するために使用され、2番目の `prob2` はフローの導関数に関連する問題です。したがって、`prob2` は次のベクトル場を実装する必要があります $\tilde F(x,y,p) = (F(x,p), dF(x,p)\cdot y)$. ```
