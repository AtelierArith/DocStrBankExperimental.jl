StopAfterNoImprovement()

監視されたメトリックが改善を停止したときにトレーニングを停止します。

パラメータ：

fn: クロージャ、ポリシーのパフォーマンスを示すスカラー値を返します（高いほど良い）。例：

1. () -> reward(env)
2. () -> total*reward*per_episode.reward

patience: 改善がないエポックの数。この数を超えるとトレーニングが停止します。

δ: 監視された量の最小変化で、改善と見なされるためのもの。すなわち、min_delta未満の絶対変化は改善なしと見なされます。

監視されたメトリックが改善を停止した後に `true` を返します。
