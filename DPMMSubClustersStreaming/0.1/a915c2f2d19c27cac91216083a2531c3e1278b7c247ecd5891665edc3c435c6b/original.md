```
dp_parallel(model_params::String; verbose = true, save_model = true,burnout = 5, gt = nothing)
```

Run the model in advanced mode.

# Args and Kwargs

  * `model_params::String` A path to a parameters file (see below)
  * `verbose` will perform prints on every iteration.
  * `save_model` will save a checkpoint every `X` iterations, where `X` is specified in the parameter file.
  * `burnout` how long to wait after creating a cluster, and allowing it to split/merge
  * `gt` Ground truth, when supplied, will perform NMI and VI analysis on every iteration.

# Return values

dp*model, iter*count , nmi*score*history, liklihood*history, cluster*count_history

  * `dp_model` The DPMM model inferred
  * `iter_count` Timing for each iteration
  * `nmi_score_history` NMI score per iteration (if gt suppled)
  * `likelihood_history` Log likelihood per iteration.
  * `cluster_count_history` Cluster counts per iteration.
