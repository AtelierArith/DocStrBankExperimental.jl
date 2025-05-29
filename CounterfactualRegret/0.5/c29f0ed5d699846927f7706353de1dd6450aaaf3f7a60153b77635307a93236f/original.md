Expected Value Baseline (Schmid 2018)

Uses aggregation counterfactual value estimates from previous runs as a baseline. "Learning rate" or exponential decay rate for learning the baseline is given by paramter α.

The stored action values for some information key `k` are retrieved by calling `(b::ExpectedValueBaseline{K})(k, l)`, where `l` is the length of the action space at the given information state represented by `k`.
