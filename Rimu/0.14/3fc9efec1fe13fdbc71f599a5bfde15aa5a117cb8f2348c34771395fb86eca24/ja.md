```
ProjectorMonteCarloProblem(hamiltonian::AbstractHamiltonian; kwargs...)
```

プロジェクター量子モンテカルロ（QMC）法によって解決される問題を定義します。例えば、[`FCIQMC`](@ref)アルゴリズムなどです。

# 一般的なキーワード引数とデフォルト:

  * `time_step = 0.01`: 初期時間ステップサイズ。
  * `last_step = 100`: ステップ数を制御します。
  * `target_walkers = 1_000`: コエフィシエントベクトルの1ノルムのターゲット。
  * `start_at = starting_address(hamiltonian)`: 初期状態ベクトルを定義します。$r × s$の状態ベクトルの行列を渡すことができ、$r$はレプリカの数、$s$はスペクトル状態の数です。[`default_starting_vector`](@ref)も参照してください。
  * `style = IsDynamicSemistochastic()`: シミュレーションの[`StochasticStyle`](@ref)。
  * `initiator = false`: イニシエーターを使用するかどうか。`true`、`false`、または有効な[`InitiatorRule`](@ref)を指定できます。
  * `threading`: デフォルトでは、利用可能な場合はマルチスレッドおよび/または[MPI](https://juliaparallel.org/MPI.jl/latest/)を使用します。`true`に設定すると、開始ベクトルに対して[`PDVec`](@ref)を強制し、`false`に設定すると直列計算になります。`start_at`によって上書きされる場合があります。
  * `reporting_strategy = ReportDFAndInfo()`: 結果を報告する方法とタイミング、[`ReportingStrategy`](@ref)を参照してください。
  * `post_step_strategy = ()`: 観測量を抽出します（例: [`ProjectedEnergy`](@ref)）、[`PostStepStrategy`](@ref)を参照してください。
  * `n_replicas = 1`: 同期された独立したシミュレーションの数。
  * `replica_strategy = NoStats(n_replicas)`: レプリカシミュレーションから報告する結果、[`ReplicaStrategy`](@ref)を参照してください。
  * `n_spectral = 1`: 対象とするスペクトル状態の数。`n_spectral > 1`に設定すると、励起状態を見つけます。
  * `spectral_strategy = GramSchmidt(n_spectral)`: スペクトル状態を直交化するために使用される[`SpectralStrategy`](@ref)。

# 例

```jldoctest
julia> hamiltonian = HubbardReal1D(BoseFS(1,2,3));

julia> problem = ProjectorMonteCarloProblem(hamiltonian; target_walkers = 500, last_step = 100);

julia> simulation = solve(problem);

julia> simulation.success[]
true

julia> size(DataFrame(simulation))
(100, 9)
```

# その他のキーワード引数:

  * `starting_step = 1`: シミュレーションの開始ステップ。
  * `wall_time = Inf`: シミュレーションに許可される最大時間。
  * `simulation_plan = SimulationPlan(; starting_step, last_step, wall_time)`: シミュレーションの期間を定義します。`last_step`および`wall_time`よりも優先されます。
  * `ζ = 0.08`: シフト更新のための減衰パラメータ。
  * `ξ = ζ^2/4`: シフト更新のための強制パラメータ。
  * `shift_strategy = DoubleLogUpdate(; target_walkers, ζ, ξ)`: `shift`を更新する方法、[`ShiftStrategy`](@ref)を参照してください。
  * `time_step_strategy = ConstantTimeStep()`: 時間ステップを調整するかどうか、`TimeStepStrategy`を参照してください。
  * `algorithm = FCIQMC(; shift_strategy, time_step_strategy)`: 使用するアルゴリズム。現在は[`FCIQMC`](@ref)のみが実装されています。
  * `shift`: 初期シフト値またはシフト値のコレクション。デフォルトではハミルトニアンと開始ベクトルから決定されます。
  * `initial_shift_parameters`: 初期シフトパラメータまたは初期シフトパラメータのコレクション。提供された場合、`shift`を上書きします。
  * `max_length = 2 * target_walkers + 100`: ベクトルの最大長。
  * `display_name = "PMCSimulation"`: 進行状況バーに表示される名前（`ProgressLogging`経由）。
  * `metadata`: レポートに追加されるユーザー提供のメタデータ。ペアの反復可能なコレクションまたは`NamedTuple`でなければなりません。例: `metadata = ("key1" => "value1", "key2" => "value2")`。すべてのメタデータは文字列に変換されます。
  * `random_seed = true`: ランダム数生成器のシードを提供し、保存します。`true`に設定すると、`RandomDevice()`から新しいランダムシードが生成されます。数値に設定すると、この数値がシードとして使用されます。このシードは、`solve`（および`init`）によってデフォルトのランダム数生成器を再シードするために使用されます（各MPIランクで一貫して）ので、同じ`ProjectorMonteCarloProblem`を2回解くと同一の結果が得られます。`false`に設定すると、シードは使用されず、連続したランダム数が使用されます。
  * `minimum_size = 2*num_spectral_states(spectral_strategy)`: `start_at`が提供されていない場合、スペクトル状態のシミュレーションのために開始ベクトルを構築するために使用される基底の最小サイズ。

[`init`](@ref)、[`solve`](@ref)も参照してください。
