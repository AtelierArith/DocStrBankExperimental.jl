```
lomc!(ham::AbstractHamiltonian, [v]; kwargs...) -> df, state
lomc!(state::ReplicaState, [df]; kwargs...) -> df, state
```

線形演算子モンテカルロ: `ham` の最小固有値を決定するための射影量子モンテカルロシミュレーションを実行します。シミュレーションの詳細は、オプションのキーワード引数とオプションの開始ベクトル `v` のタイプによって制御されます。あるいは、以前のシミュレーションを続行するために `ReplicaState` を渡すこともできます。

# 一般的なキーワード引数とデフォルト:

  * `laststep = 100` - ステップ数を制御します。
  * `dτ = 0.01` - タイムステップ。
  * `targetwalkers = 1000` - コエフィシエントベクトルの1ノルムのターゲット。
  * `address = starting_address(ham)` - デフォルトの `v` と `shift` の開始アドレスを設定します。
  * `style = IsStochasticInteger()` - デフォルトの `v` のための [`StochasticStyle`](@ref) を設定します; `v` が指定されている場合は未使用。
  * `initiator = NonInitiator()` - デフォルトの `v` のための [`InitiatorRule`](@ref) を設定します; `v` が指定されている場合は未使用。
  * `threading` - デフォルトは、複数のスレッドが利用可能な場合にマルチスレッドと [MPI](https://juliaparallel.org/MPI.jl/latest/) を使用します。`true` に設定すると、開始ベクトルのために [`PDVec`](@ref) を強制し、`false` に設定すると直列計算を行います; `v` が指定されている場合は未使用。
  * `shift = diagonal_element(ham, address)` - シフトの初期値。
  * `post_step_strategy::NTuple{N,<:PostStepStrategy} = ()` - 観測量を抽出します (例: [`ProjectedEnergy`](@ref)), [`PostStepStrategy`](@ref) を参照してください。 (非推奨: `post_step` は `post_step_strategy` のエイリアスとして受け入れられます。)
  * `replica_strategy::ReplicaStrategy = NoStats(1)` - 複数の同期シミュレーションを実行します; [`ReplicaStrategy`](@ref) を参照してください。 (非推奨: `replica` は `replica_strategy` のエイリアスとして受け入れられます。)
  * `reporting_strategy::ReportingStrategy = ReportDFAndInfo()` - 結果を報告する方法とタイミング; [`ReportingStrategy`](@ref) を参照してください。 (非推奨: `r_strat` は `reporting_strategy` のエイリアスとして受け入れられます。)
  * `name = "lomc!"` - 進行状況バーに表示される名前 ( `ProgressLogging` を介して)
  * `metadata` - レポート `df` に追加されるユーザー提供のメタデータ。ペアの反復可能なものまたは `NamedTuple` でなければなりません。例: `metadata = ("key1" => "value1", "key2" => "value2")`。すべてのメタデータは文字列に変換されます。

一部のメタデータは、[`Rimu.PACKAGE_VERSION`](@ref) や `state` からのデータを含むレポート `df` に自動的に追加されます。

# 戻り値

`lomc!` は次のフィールドを持つ名前付きタプルを返します:

  * `df`: 報告されるすべての統計を含む `DataFrame`。
  * `state`: 継続に使用できる `ReplicaState`。

# 例

```jldoctest
julia> address = BoseFS(1,2,3);

julia> hamiltonian = HubbardReal1D(address);

julia> df1, state = @suppress lomc!(hamiltonian; targetwalkers=500, laststep=100);

julia> df2, _ = @suppress lomc!(state, df1; laststep=200, metadata=(;info="cont")); # 継続実行

julia> size(df1)
(100, 9)

julia> size(df2)
(200, 9)

julia> using DataFrames; metadata(df2, "info") # カスタムメタデータを取得
"cont"

julia> metadata(df2, "hamiltonian") # 一部のメタデータは自動的に追加されます
"HubbardReal1D(fs\"|1 2 3⟩\"; u=1.0, t=1.0)"
```

# その他のキーワード引数とデフォルト:

  * `τ_strat::TimeStepStrategy = ConstantTimeStep()` - タイムステップを調整するかどうか; [`TimeStepStrategy`](@ref) を参照してください。
  * `s_strat::ShiftStrategy = DoubleLogUpdate(; target_walkers=targetwalkers, ζ = 0.08, ξ = ζ^2/4)` - `shift` を更新する方法; [`ShiftStrategy`](@ref) を参照してください。
  * `maxlength = 2 * s_strat.target_walkers + 100` - `v` の長さの上限; 到達した場合、`lomc!` は中止します。
  * `wm` - 後続の計算で再利用するための作業メモリ; 変更されます。
  * `df = DataFrame()` - `AbstractHamiltonian` 引数で呼び出された場合、レポート `df` とマージするために `DataFrame` を渡すことができます。

開始ベクトルのデフォルトの選択は `v = default_starting_vector(; address, style, threading, initiator)` です。 [`default_starting_vector`](@ref), [`PDVec`](@ref), [`DVec`](@ref), [`StochasticStyle`](@ref), および [`InitiatorRule`](@ref) を参照してください。

!!! warning
    この `lomc!` の使用は非推奨です。代わりに [`ProjectorMonteCarloProblem`](@ref) と [`solve`](@ref) を使用してください。

