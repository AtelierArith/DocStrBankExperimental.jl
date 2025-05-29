```
get_randomisations(d::Design, min_randomisations::Integer, target_shot_budget::Integer, experiment_shots::Integer; p_norm::Real = 2)
```

実験デザイン `d` の各タプルに対するランダム化の数を返します。これは、ターゲットショット予算 `target_shot_budget`、各実験のショット数 `experiment_shots`、および最小ランダム化数 `min_randomisations` に基づいています。ランダム化の数は、実験デザインに関連するショットウェイトに対して `p_norm`-ノルムを最小化するように貪欲に最適化されます。

通常、2-ノルムは小さいショット予算に対してより効果的であり、1-ノルムは大きいショット予算に対してより効果的です。ランダム化の数は、正規化されていないショットウェイト `randomisations .* d.experiment_numbers` に対応します。
