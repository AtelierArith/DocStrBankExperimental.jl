```
plot_evolution(
    payoff_functions::Tuple{Function, Function, Function},
    x0_list::Vector{<:AbstractVector{<:Real}},
    tspan::Tuple{Float64, Float64};
    labels::Vector{String} = ["戦略 1", "戦略 2", "戦略 3"],
    extra_params::NamedTuple = NamedTuple(),
    steady_state_tol::Float64 = 1e-6,
    arrow_list::Vector{Vector{Int}} = Vector{Vector{Int}}(),
    trajectory_labels::Vector{String} = String[],
    trajectory_colors::AbstractVector = Any[],
    trajectory_linewidth::Int = 2,
    num_initial_guesses::Int = 1000,
    solver_tol::Float64 = 1e-8,
    equilibrium_tol::Float64 = 1e-5,
    validity_tol::Float64 = 1e-6,
    stability_tol::Float64 = 1e-6,
    markersize::Int = 9,
    markerstrokewidth::Int = 2,
    colored_trajectories::Bool = false,
    contour::Bool = false,
    contour_color::Symbol = :roma,
    contour_resolution::Int = 150,
    contour_levels::Int = 10,
    colorbar::Bool = false,
    triangle_linewidth::Int = 2,
    legend::Bool = false,
    margin::Int = 2,
    dpi::Int = 300,
)::Plots.Plot
```

3戦略のシンプレックス内でのレプリケーターダイナミクスの軌道をシミュレートし、均衡を特定し、結果の三角プロットを作成します。

# 引数

  * `payoff_functions`: 3つのペイオフ関数のタプル `(payoff1, payoff2, payoff3)` で、それぞれが `(x, t, params)` を受け取り、`x` は正規化された頻度ベクトルです。
  * `x0_list`: シンプレックス内の初期条件のコレクション（各長さ3のベクトル）。これらの初期点から各軌道がシミュレートされます。
  * `tspan`: 積分ウィンドウを指定するタプル `(tstart, tfinal)` です。
  * `labels`: 三角形の角のラベル。デフォルトは `["戦略 1", "戦略 2", "戦略 3"]` です。
  * `extra_params`: ペイオフ関数に渡される追加のパラメータで、`NamedTuple` にパッケージ化されています。
  * `steady_state_tol`: 導関数のノルムがこの閾値を下回ると、ソルバーは早期に停止します（コールバックを介して）。
  * `arrow_list`: 各軌道に沿って矢印を描画するインデックスを指定する配列の配列です。
  * `trajectory_labels`: 凡例が必要な場合の各軌道のラベル。デフォルトは "Trajectory i" で、i は `1:length(x0_list)` の範囲です。
  * `trajectory_colors`: 軌道の色。空の場合、すべての軌道は黒で、`colored_trajectories` が真の場合は tab10 パレットが使用されます。
  * `trajectory_linewidth`: 軌道をプロットするために使用される線の幅です。
  * `num_initial_guesses`: 均衡を特定するためのルート探索のためのランダムな初期推測の数です。
  * `solver_tol`: 均衡を見つけるための非線形ソルバーによって内部的に使用される許容誤差です。
  * `equilibrium_tol`: 2つの均衡が実質的に同じであると宣言するための許容誤差です。
  * `validity_tol`: 点がシンプレックス内にあると見なされるための許容誤差 (0 ≤ xᵢ ≤ 1) です。
  * `stability_tol`: すべての固有値が負の実部を持つかどうかを判断する際に使用される許容誤差（安定）。
  * `markersize`: 均衡マーカーのサイズです。
  * `markerstrokewidth`: 均衡マーカーの境界のストローク幅です。
  * `colored_trajectories`: `true` の場合、各軌道を異なる色で色付けします。そうでない場合は、単一の色を使用します。
  * `contour`: 平均ペイオフの等高線プロットを重ねるかどうか。`true` の場合、`scatter` を使用して各シンプレックスグリッドポイントをその平均ペイオフで色付けします。
  * `contour_color`: 等高線プロットの色のグラデーションを表すシンボル（例: `:viridis`, `:roma`）です。
  * `contour_resolution`: 等高線プロットのためのシンプレックスグリッドの解像度です。
  * `contour_levels`: 表示する等高線レベルの数（色のスケーリングに使用されます）。
  * `colorbar`: `contour` が `true` の場合にカラーバーを表示するかどうか。
  * `triangle_linewidth`: シンプレックス境界線の線幅です。
  * `legend`: 軌道ラベルの凡例を表示するかどうか。
  * `margin`: 等高線ポイントを計算およびプロットする際に、シンプレックスグリッドのエッジからスキップする行/列の数（境界の重なりを避けるため）。
  * `dpi`: 最終プロットの解像度です。

# 戻り値

  * 次の内容を持つ `Plots.Plot` オブジェクト：

    1. シンプレックス内の平均ペイオフの（オプションの）等高線プロット。
    2. シンプレックスの辺（中立の辺がオプションで強調表示される）。
    3. 提供された初期条件からのシミュレートされた軌道。
    4. 検出された均衡は、安定している場合は塗りつぶされた円、非安定の場合は空の円でマークされます。

# 注意事項

  * 内部的に `identify_neutral_edges` を呼び出して、2つの戦略間のペイオフがその辺に沿ったすべての点で等しい辺を強調表示します。
  * 均衡は `find_equilibria` で特定され、各均衡はヤコビアンを分析することで安定性がテストされます。
  * 矢印の描画は `arrow0!` によって処理され、`arrow_list` でユーザー指定の矢印位置が使用されます。
