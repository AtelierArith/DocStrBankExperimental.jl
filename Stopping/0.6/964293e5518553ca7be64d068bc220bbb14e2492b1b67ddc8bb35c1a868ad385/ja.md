タイプ: StoppingMeta

メソッド: メソッドはありません。

属性:

  * `atol`: 絶対許容誤差。
  * `rtol`: 相対許容誤差。
  * `optimality0`: 初期推定値での最適性スコア。
  * `tol_check`: スコアをゼロにテストするための `atol`、`rtol` および `optimality0` の関数。
  * `tol_check_neg`: スコアをゼロにテストするための `atol`、`rtol` および `optimality0` の関数。
  * `check_pos`: 正の許容誤差のための事前割り当て
  * `check_neg`: 負の許容誤差のための事前割り当て
  * `recomp_tol`: 許容誤差が更新された場合は真。
  * `optimality_check`: 許容関数を介した停止基準。
  * `unbounded_threshold`: 問題の無限大の閾値。
  * `unbounded_x`: 反復の無限大の閾値。
  * `max_f`: 関数（および導関数）評価の最大数。
  * `max_cntrs`: 最大評価数を含む辞書。
  * `max_eval`: 関数（および導関数）評価の最大数。
  * `max_iter`: `stop!` 呼び出し/反復の数に関する閾値。
  * `max_time`: アルゴリズムの実行を許可する時間制限。
  * `nb_of_stop`: `stop!` 呼び出し/反復の数を追跡。
  * `start_time`: 開始時の時間を追跡。
  * `fail_sub_pb`: ステータス。
  * `unbounded`: ステータス。
  * `unbounded_pb`: ステータス。
  * `tired`: ステータス。
  * `stalled`: ステータス。
  * `iteration_limit`: ステータス。
  * `resources`: ステータス。
  * `optimal`: ステータス。
  * `infeasible`: ステータス。
  * `main_pb`: ステータス。
  * `domainerror`: ステータス。
  * `suboptimal`: ステータス。
  * `stopbyuser`: ステータス。
  * `exception`: ステータス。
  * `meta_user_struct`:  任意
  * `user_check_func!`: 関数 (AbstractStopping, Bool) -> コールバック。

`StoppingMeta(;atol :: Number = 1.0e-6, rtol :: Number = 1.0e-15, optimality0 :: Number = 1.0, tol_check :: Function = (atol,rtol,opt0) -> max(atol,rtol*opt0), tol_check_neg :: Function = (atol,rtol,opt0) -> -max(atol,rtol*opt0), unbounded_threshold :: Number = 1.0e50, unbounded_x :: Number = 1.0e50, max_f :: Int = typemax(Int), max_eval :: Int = 20000, max_iter :: Int = 5000, max_time :: Number = 300.0, start_time :: Float64 = NaN, meta_user_struct :: Any = nothing, kwargs...)`

定数許容誤差を持つ代替:

`StoppingMeta(tol_check :: T, tol_check_neg :: T;atol :: Number = 1.0e-6, rtol :: Number = 1.0e-15, optimality0 :: Number = 1.0, unbounded_threshold :: Number = 1.0e50, unbounded_x :: Number = 1.0e50, max_f :: Int = typemax(Int), max_eval :: Int = 20000, max_iter :: Int = 5000, max_time :: Number = 300.0, start_time :: Float64 = NaN, meta_user_struct :: Any = nothing, kwargs...)`

注意:

  * これは可変構造体であるため、`StoppingMeta` の要素を変更できます。
  * `nb_of_stop` は、`stop!` または `update_and_stop!` が呼び出されるたびにインクリメントされます。
  * `optimality0` はアルゴリズムの開始時に一度変更されます（`start!`）。
  * `start_time` は、事前に指定されていない場合、アルゴリズムの開始時に一度変更されます（`start!`）。
  * 異なるステータス: `fail_sub_pb`、`unbounded`、`unbounded_pb`、`tired`、`stalled`、`iteration_limit`、`resources`、`optimal`、`main_pb`、`domainerror`、`suboptimal`、`infeasible`
  * `fail_sub_pb`、`suboptimal`、および `infeasible` はアルゴリズムによって変更されます。
  * `optimality_check` は二つの入力を受け取ります（`AbstractNLPModel`、`NLPAtX`）そして `0` と比較される `Number` または `AbstractVector` を返します。
  * `optimality_check` は必ずしも状態を埋めるわけではありません。

例: `StoppingMeta()`, `StoppingMeta(1., -1.)`
