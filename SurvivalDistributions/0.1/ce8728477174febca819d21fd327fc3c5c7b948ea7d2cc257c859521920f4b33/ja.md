hazard(X::UnivariateDistribution, t)

確率変数 X のハザード関数を点 t で提供します（`Distributions.ContinuousUnivariateDistributions` であると仮定）。デフォルトの実装は単に $vh(t) = \frac{f(t)}{S(t)}$ であり、ここで $f$ は X の密度関数、$S$ は生存関数です。
