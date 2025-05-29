StopAfterNoImprovement()

Stop training when a monitored metric has stopped improving.

Parameters:

fn: a closure, return a scalar value, which indicates the performance of the policy (the higher the better) e.g.

1. () -> reward(env)
2. () -> total*reward*per_episode.reward

patience: Number of epochs with no improvement after which training will be stopped.

δ: Minimum change in the monitored quantity to qualify as an improvement, i.e. an absolute change of less than min_delta, will count as no improvement.

Return `true` after the monitored metric has stopped improving.
