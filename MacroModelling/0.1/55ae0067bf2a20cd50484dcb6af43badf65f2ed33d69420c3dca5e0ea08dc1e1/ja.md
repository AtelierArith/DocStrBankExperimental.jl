```julia
Tolerances(
;
    NSSS_acceptance_tol,
    NSSS_xtol,
    NSSS_ftol,
    NSSS_rel_xtol,
    qme_tol,
    qme_acceptance_tol,
    sylvester_tol,
    sylvester_acceptance_tol,
    lyapunov_tol,
    lyapunov_acceptance_tol,
    droptol,
    dependencies_tol
)

```

さまざまな問題のソルバーのために手動で許容値を定義する関数：非確率定常状態ソルバー（NSSS）、シルベスター方程式、リャプノフ方程式、および二次行列方程式（qme）。

# キーワード引数

  * `NSSS_acceptance_tol` [デフォルト: `1e-12`, タイプ: `AbstractFloat`]: 非確率定常状態ソルバーの受け入れ許容値。
  * `NSSS_xtol` [デフォルト: `1e-12`, タイプ: `AbstractFloat`]: 非確率定常状態ソルバーのソルバーステップの絶対許容値。
  * `NSSS_ftol` [デフォルト: `1e-14`, タイプ: `AbstractFloat`]: 非確率定常状態ソルバーのソルバーファンクション値の絶対許容値。
  * `NSSS_rel_xtol` [デフォルト: `eps()`, タイプ: `AbstractFloat`]: 非確率定常状態ソルバーのソルバーステップの相対許容値。
  * `qme_tol` [デフォルト: `1e-14`, タイプ: `AbstractFloat`]: 二次行列方程式ソルバーの許容値。
  * `qme_acceptance_tol` [デフォルト: `1e-8`, タイプ: `AbstractFloat`]: 二次行列方程式ソルバーの受け入れ許容値。
  * `sylvester_tol` [デフォルト: `1e-14`, タイプ: `AbstractFloat`]: シルベスター方程式ソルバーの許容値。
  * `sylvester_acceptance_tol` [デフォルト: `1e-10`, タイプ: `AbstractFloat`]: シルベスター方程式ソルバーの受け入れ許容値。
  * `lyapunov_tol` [デフォルト: `1e-14`, タイプ: `AbstractFloat`]: リャプノフ方程式ソルバーの許容値。
  * `lyapunov_acceptance_tol` [デフォルト: `1e-12`, タイプ: `AbstractFloat`]: リャプノフ方程式ソルバーの受け入れ許容値。
  * `droptol` [デフォルト: `1e-14`, タイプ: `AbstractFloat`]: 行列のエントリが0と見なされる許容値。
  * `dependencies_tol` [デフォルト: `1e-12`, タイプ: `AbstractFloat`]: 共分散関連の統計を計算するためにシステムの一部を分離する際に、変数が関心のある変数に与える影響の許容値。
