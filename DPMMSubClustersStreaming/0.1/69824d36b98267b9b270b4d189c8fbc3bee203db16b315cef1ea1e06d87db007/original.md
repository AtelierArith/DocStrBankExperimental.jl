```
dp_parallel(all_data::AbstractArray{Float32,2},
    local_hyper_params::distribution_hyper_params,
    α_param::Float32,
     iters::Int64 = 100,
     init_clusters::Int64 = 1,
     seed = nothing,
     verbose = true,
     save_model = false,
     burnout = 15,
     gt = nothing,
     max_clusters = Inf,
     outlier_weight = 0,
     outlier_params = nothing)
```

Run the model.

# Args and Kwargs

  * `all_data::AbstractArray{Float32,2}` a `DxN` array containing the data
  * `local_hyper_params::distribution_hyper_params` the prior hyperparams
  * `α_param::Float32` the concetration parameter
  * `iters::Int64` number of iterations to run the model
  * `init_clusters::Int64` number of initial clusters
  * `seed` define a random seed to be used in all workers, if used must be preceeded with `@everywhere using random`.
  * `verbose` will perform prints on every iteration.
  * `save_model` will save a checkpoint every 25 iterations.
  * `burnout` how long to wait after creating a cluster, and allowing it to split/merge
  * `gt` Ground truth, when supplied, will perform NMI and VI analysis on every iteration.
  * `max_clusters` limit the number of cluster
  * `outlier_weight` constant weight of an extra non-spliting component
  * `outlier_params` hyperparams for an extra non-spliting component

# Return values

dp*model, iter*count , nmi*score*history, liklihood*history, cluster*count_history

  * `dp_model` The DPMM model inferred
  * `iter_count` Timing for each iteration
  * `nmi_score_history` NMI score per iteration (if gt suppled)
  * `likelihood_history` Log likelihood per iteration.
  * `cluster_count_history` Cluster counts per iteration.
