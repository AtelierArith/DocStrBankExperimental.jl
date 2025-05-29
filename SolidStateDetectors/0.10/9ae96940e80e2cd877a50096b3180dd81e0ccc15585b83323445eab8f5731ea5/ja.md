```
calculate_weighting_potential!(sim::Simulation{T}, contact_id::Int; kwargs...)::Nothing
```

[`WeightingPotential`](@ref)を、`contact_id`を持つ[`Contact`](@ref)のために、適応グリッド上での逐次過剰緩和を通じて計算し、`sim.weighting_potentials[contact_id]`に格納します。

計算を調整するために使用できるいくつかのキーワード引数があります。

## キーワード

  * `convergence_limit::Real`: `convergence_limit`は、緩和の収束限界を設定します。収束値は、すべてのグリッドポイントの2回の反復間のポテンシャルの絶対最大差です。`convergence_limit`のデフォルトは`1e-7`です。
  * `refinement_limits`: 各次元の隣接するグリッドポイントのポテンシャル値の最大相対許容差を定義します。

      * `rl::Real` -> すべての3次元で`rl`が等しい1つのリファインメント。
      * `rl::Tuple{<:Real,<:Real,<:Real}` -> 各次元ごとに個別に設定された`rl`の1つのリファインメント。
      * `rl::Vector{<:Real}` -> `length(l)`のリファインメントで、`rl[i]`がi番目のリファインメントの限界です。
      * `rl::Vector{<:Real,<:Real,<:Real}}` -> `length(rl)`のリファインメントで、`rl[i]`がi番目のリファインメントの限界です。
  * `min_tick_distance::Tuple{<:Quantity, <:Quantity, <:Quantity}`: 各次元の2つのグリッドティック間の最小許容距離のタプルです。リファインメントがグリッドを細かくしすぎるのを防ぎます。デフォルトは線形軸で`1e-5`、円筒形の`grid`の場合は極軸で`1e-5 / (0.25 * r_max)`です。
  * `max_tick_distance::Tuple{<:Quantity, <:Quantity, <:Quantity}`: グリッドの初期化に使用される各次元の2つのグリッドティック間の最大許容距離のタプルです。デフォルトはそれぞれの次元の世界のサイズの1/4です。
  * `max_distance_ratio::Real`: 2つの隣接するグリッドポイント間の任意の次元における2つの距離の最大許容比です。比が大きすぎる場合、新しい比が`max_distance_ratio`より小さくなるように追加のティックが生成されます。デフォルトは`5`です。
  * `grid::Grid`: シミュレーションを開始するために使用される初期グリッドです。デフォルトは`Grid(sim)`です。
  * `depletion_handling::Bool`: 未枯渇領域の処理を有効にします。デフォルトは`false`です。これは実験的な機能です：未枯渇領域（`calculate_electric_potential!(sim; depletion_handling = true)`で決定される）では、半導体の誘電率がスケールアップされて導電的な挙動を模倣します。スケールファクターは[`scaling_factor_for_permittivity_in_undepleted_region`](@ref)関数を介して調整できます。
  * `use_nthreads::Union{Int, Vector{Int}}`: `<:Int`の場合、`use_nthreads`は計算に使用される最大スレッド数を定義します。スレッドのオーバーヘッドにより、現在のグリッドサイズに応じて少ないスレッドが使用される場合があります。デフォルトは`Base.Threads.nthreads()`です。`<:Vector{Int}`の場合、`use_nthreads[i]`はフィールドシミュレーションの各グリッド（リファインメント）ステージで使用されるスレッド数を定義します。環境変数`JULIA_NUM_THREADS`は、Juliaセッションが開始される前に適切に設定されている必要があります（例：bashの場合`export JULIA_NUM_THREADS=8`）。
  * `sor_consts::Union{<:Real, NTuple{2, <:Real}}`: 円筒座標の場合の2要素タプルです。最初の要素は`r` = 0のSOR定数を含みます。2番目の要素は`r`の最外部グリッドポイントでの定数を含みます。その間に線形スケーリングが適用されます。最初の要素は2番目の要素より小さく、両方とも`∈ [1.0, 2.0]`である必要があります。デフォルトは`[1.4, 1.85]`です。直交座標の場合は、1つの値のみが取られます。
  * `max_n_iterations::Int`: 各グリッドリファインメントの後に実行される最大反復回数を設定します。デフォルトは`10000`です。`-1`に設定すると制限はありません。
  * `not_only_paint_contacts::Bool = true`: [`Contact`](@ref)の表面のペインティングアルゴリズムのみを使用するかどうかを示します。`false`に設定するとパフォーマンスが向上しますが、[`Contact`](@ref)の内部にあるポイントはもはや固定されません。
  * `paint_contacts::Bool = true`: [`Contact`](@ref)の表面を`grid`にペイントすることを有効または無効にします。
  * `verbose::Bool=true`: 情報出力が生成されるかどうかのブール値です。

## 例

```julia
calculate_weighting_potential!(sim, 1, refinement_limits = [0.3, 0.1, 0.05], max_distance_ratio = 4, max_n_iterations = 20000)
```
