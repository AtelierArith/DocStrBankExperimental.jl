```
SolverOptions{T}

プライマル-デュアル内部点ソルバーのオプションと許容値。

rtol: 残差違反（等式制約）に対する許容値；デフォルトは1e-6
btol: バイリニア違反（補完制約）に対する許容値；デフォルトは1e-4
ls_scale: ラインサーチスケーリングファクター (α_new ← ls_scale * α_current)；デフォルトは0.5
max_iter: ニュートン反復の最大数；デフォルトは50
max_ls: ラインサーチステップの最大数；デフォルトは10
undercut: 補完性のスラックネス目標；ソルバーは補完性違反 = btol / undercut に到達することを目指す；デフォルトはInf
no_progress_max: 進展のないニュートン反復の数が目標補完性違反の再スケーリングを引き起こす；デフォルトは3
no_progress_undercut: アンダーカットスケーリングファクター (target_new ← target_current / no_progress_undercut)；デフォルトは10
verbose: 解決中のソルバーの状態を印刷するためのフラグ；デフォルトはfalse
```
