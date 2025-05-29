```
fit(all_data::AbstractArray{Float32,2},local_hyper_params::distribution_hyper_params,α_param::Float32;
   iters::Int64 = 100, init_clusters::Int64 = 1,seed = nothing, verbose = true, save_model = false, burnout = 20, gt = nothing, max_clusters = Inf, outlier_weight = 0, outlier_params = nothing,smart_splits = false)
```

Run the model (basic mode).

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
  * `smart_splits` should use smart splits (Gaussian only, default is false)

# Return Values

  * `labels` Labels assignments
  * `clusters` Cluster parameters
  * `weights` The cluster weights, does not sum to `1`, but to `1` minus the weight of all uninstanistaed clusters.
  * `iter_count` Timing for each iteration
  * `nmi_score_history` NMI score per iteration (if gt suppled)
  * `likelihood_history` Log likelihood per iteration.
  * `cluster_count_history` Cluster counts per iteration.
  * `sub_labels` Sub labels assignments

# Example:

```julia
julia> x,y,clusters = generate_gaussian_data(10000,2,6,100.0)
...

julia> hyper_params = DPMMSubClusters.niw_hyperparams(1.0,
                  zeros(2),
                  5,
                  [1 0;0 1])
DPMMSubClusters.niw_hyperparams(1.0f0, Float32[0.0, 0.0], 5.0f0, Float32[1.0 0.0; 0.0 1.0])

julia> ret_values= fit(x,hyper_params,10.0, iters = 100, verbose=false)

...

julia> unique(ret_values[1])
6-element Array{Int64,1}:
 3
 6
 1
 2
 5
 4
```
