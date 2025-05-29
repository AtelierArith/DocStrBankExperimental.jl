```julia
mutable struct EAGOParameters
```

グローバルソルブ中に変更されないパラメータのストレージ。

  * `presolve_scrubber_flag::Bool`: EAGOがユーザー定義関数の型アサート問題を削除しようとするべきか（デフォルト = false）
  * `presolve_to_JuMP_flag::Bool`: ユーザー定義関数のDAG表現を作成して使用する（デフォルト = false）
  * `presolve_flatten_flag::Bool`: 登録された変換を使用してDAGを再配置する（デフォルト = false）
  * `conic_convert_quadratic::Bool`: 凸制約を二次円錐に橋渡ししようとする（デフォルト = false）
  * `log_on::Bool`: ロギングをオンにする; グローバルバウンド、ノード数、実行時間を記録する。サブプロブレムに特有の情報を記録するための追加オプションが利用可能（デフォルト = false）
  * `log_subproblem_info::Bool`: サブプロブレムの時間と実現可能性のロギングをオンにする（デフォルト = false）
  * `log_interval::Int64`: `log_interval`イテレーションごとにデータをログする（デフォルト = 1）
  * `verbosity::Int64`: 解決中にコンソールに印刷される情報の量。値は0 - 4の範囲: 0はサイレント、1はイテレーションの要約統計のみを表示、2-4は各イテレーション内の計算に関するさまざまな詳細度を表示（デフォルト = 1）
  * `output_iterations::Int64`: `output_iterations`ごとにイテレーションの要約をコンソールに表示（デフォルト = 1000）
  * `header_iterations::Int64`: `output_iterations`ごとに要約のヘッダーをコンソールに表示（デフォルト = 100000）
  * `branch_cvx_factor::Float64`: ブランチポイントを選択するために使用される凸係数。ブランチポイントは`branch_cvx_factor*xmid + (1-branch_cvx_factor)*xsol`によって与えられる（デフォルト = 0.25）
  * `branch_offset::Float64`: ブランチポイントを持つための境界からの最小距離、ブランチする次元の幅で正規化（デフォルト = 0.15）
  * `branch_pseudocost_on::Bool`: 擬似コストブランチを使用することを示す（デフォルト = false）
  * `branch_variable::Vector{Bool}`: ブランチする変数（デフォルトはすべて非線形）
  * `branch_max_repetitions::Int64`: [将来の機能、現在は実装されていない] ブランチする前にノード処理を繰り返す回数（デフォルト = 4）
  * `branch_repetition_tol::Float64`: [将来の機能、現在は実装されていない] 現在のノードを繰り返し処理するために必要な体積比の許容値（デフォルト = 0.9）
  * `node_limit::Int64`: 最大ノード数（デフォルト = 1E7）
  * `time_limit::Float64`: 最大CPU時間（秒単位）（デフォルト = 3600）
  * `iteration_limit::Int64`: 最大イテレーション数（デフォルト 1E9）
  * `absolute_tolerance::Float64`: 終了のための絶対許容値（デフォルト = 1E-3）
  * `relative_tolerance::Float64`: 終了のための相対許容値（デフォルト = 1E-3）
  * `absolute_constraint_feas_tolerance::Float64`: 絶対制約実現可能性許容値（デフォルト = 1E-8）
  * `cp_depth::Int64`: 制約伝播を無効にすべきB&Bツリーの深さ（デフォルト = 0）
  * `cp_repetitions::Int64`: フォワード-リバースパスルーチンを繰り返す回数（デフォルト = 0）
  * `cp_tolerance::Float64`: 新しいノードの体積と開始ノードの体積の比がこの数を超えた場合、制約伝播を無効にする（デフォルト = 0.99）
  * `cp_interval_only::Bool`: 制約伝播中に有効な区間境界のみを使用する（デフォルト = false）
  * `obbt_depth::Int64`: OBBTを無効にすべきB&Bツリーの深さ（デフォルト = 6）
  * `obbt_repetitions::Int64`: 前処理で実行するOBBTの繰り返し回数（デフォルト = 3）
  * `obbt_aggressive_on::Bool`: 攻撃的なOBBTをオンにする（デフォルト = true）
  * `obbt_aggressive_max_iteration::Int64`: 攻撃的なOBBTを実行する最大イテレーション（デフォルト = 2）
  * `obbt_aggressive_min_dimension::Int64`: 攻撃的なOBBTを実行する最小次元（デフォルト = 2）
  * `obbt_tolerance::Float64`: 境界を等しいと見なすための許容値（デフォルト = 1E-10）
  * `fbbt_lp_depth::Int64`: 線形FBBTを無効にすべきB&Bツリーの深さ（デフォルト = 1000）
  * `fbbt_lp_repetitions::Int64`: 前処理で実行する線形FBBTの繰り返し回数（デフォルト = 3）
  * `dbbt_depth::Int64`: 双対ベースの境界引き締めを無効にすべきB&Bツリーの深さ（デフォルト = 1E10）
  * `dbbt_tolerance::Float64`: 新しい境界は、dbbt_tolerance内であれば以前の境界と等しいと見なされる（デフォルト = 1E-8）
  * `relax_tag::McCormick.RelaxTag`: McCormick演算子のタイプを指定するために使用されるRelaxTag（デフォルト = NS()）
  * `subgrad_tighten::Bool`: フォワードパス中に各非線形テープの各因子でサブ勾配を使用して区間境界を引き締める（デフォルト = true）
  * `reverse_subgrad_tighten::Bool`: リバースパス中に各非線形テープの各因子でサブ勾配を使用して区間境界を引き締める（デフォルト = false）
  * `subgrad_tol::Float64`: 外部ラウンドで計算されたサブ勾配境界をこの量だけ（デフォルト = 1E-10）
  * `mul_relax_style::Int64`: 二項項（乗算）に使用する緩和のタイプを選択する: 0は標準的なMcCormick算術アプローチに対応。設定1-3は、標準的なMcCormick緩和を暗示された事前緩和で増強する: (1)はサブ勾配ベースの事前緩和アプローチに対応; (2)はアフィン算術ベースの事前アプローチに対応; (3)は列挙的事前緩和ベースのアプローチに対応（デフォルト = 0）
  * `cut_min_iterations::Int64`: 各ノードで試みるカットの最小数（安全でないカットが必ずしも追加されるわけではない）（デフォルト = 2）
  * `cut_max_iterations::Int64`: 各ノードで試みるカットの最大数（デフォルト = 8）
  * `cut_tolerance_abs::Float64`: 続行するカットのためにチェックされる絶対許容値（デフォルト = 1E-6）
  * `cut_tolerance_rel::Float64`: 続行するカットのためにチェックされる相対許容値（デフォルト = 1E-3）
  * `cut_safe_on::Bool`: Khajavirad 2018の方法で安全なカットを決定するために許容値を使用する（デフォルト = true）
  * `cut_safe_l::Float64`: 安全なlpカットのための下限許容値、Khajavirad 2018（デフォルト = 1E-7）
  * `cut_safe_u::Float64`: 安全なlpカットのための上限許容値、Khajavirad 2018（デフォルト = 1E7）
  * `cut_safe_b::Float64`: 安全なlpカットのための定数許容値、Khajavirad 2018（デフォルト = 1E9）
  * `upper_bounding_depth::Int64`: `upper_bounding_depth`未満の深さの各ノードに対して上位問題を解決し、それ以外の場合は深さが`upper_bounding_depth`を超える確率で上位問題を解決する（デフォルト = 8）
  * `domain_violation_guard_on::Bool`: （未使用）ドメイン違反から保護する（デフォルト = false）
  * `domain_violation_ϵ::Float64`: （未使用）境界を伝播する際に無視するドメイン違反の量（デフォルト = 1E-9）
  * `user_solver_config::Bool`: trueの場合、EAGOはサブソルバーのためのデフォルト設定プロセスを省略する（デフォルト = false）
  * `integer_abs_tol::Float64`: 決定変数の整数性をチェックするために使用される絶対許容値（デフォルト = 1E-9）
  * `integer_rel_tol::Float64`: 決定変数の整数性をチェックするために使用される相対許容値（デフォルト = 1E-9）
  * `force_global_solve::Bool`: EAGOの問題タイプを解析する能力を無視し、グローバル最適化を強制的に実行する（デフォルト = false）
  * `unbounded_check::Bool`: すべてのブランチ変数が有限の境界を持っていることを確認し、そうでない場合はそれらを+/- 1E10に設定する（デフォルト = true）
