```
	solvesdp(problem::Problem; kwargs...)
```

```
    solvesdp(sdp::ClusteredLowRankSDP; kwargs...)
```

`problem` または `sdp` から生成された半正定値計画を解きます。

キーワード引数:

  * `prec` (デフォルト: `precision(BigFloat)`): 使用される精度
  * `gamma` (デフォルト: `0.9`): ステップ長の減少; 最大ステップ長 α は `max(gamma*α,1)` に減少します
  * `beta_(in)feasible` (デフォルト: `0.1` (`0.3`)): 各反復で mu を減少させようとする量、(in)feasible ソリューションのため
  * `omega_p/d` (デフォルト: `10^10`): プライマル/双対の開始行列変数は `omega_p/d*I`
  * `maxiterations` (デフォルト: `500`): 最大反復回数
  * `duality_gap_threshold` (デフォルト: `10^-15`): 解が最適にどれだけ近い必要があるか
  * `primal/dual_error_threshold` (デフォルト:`10^-30`): プライマル/双対解がどれだけ実現可能である必要があるか
  * `max_complementary_gap` (デフォルト: `10^100`): 許可される `dot(X,Y)/nrows(X)` の最大値
  * `need_primal_feasible/need_dual_feasible` (デフォルト: `false`): 解がプライマル/双対実現可能なときに終了
  * `verbose` (デフォルト: `true`): true の場合、各反復後に情報を印刷
  * `step_length_threshold` (デフォルト: `10^-7`): 許可される最小ステップ長
  * `primalsol` (デフォルト: `nothing`): `primalsol` と `dualsol` の両方が与えられた場合、解 `(primalsol, dualsol)` から開始
  * `dualsol` (デフォルト: `nothing`): `primalsol` と `dualsol` の両方が与えられた場合、解 `(primalsol, dualsol)` から開始
  * `safe_step` (デフォルト: `true`): ステップ長が最大1の「安全な」ステップのみを使用し、解がプライマルおよび双対実現可能な場合は alpha*p = alpha*d を取ります
