```
hc_partition_groups(X::AbstractMatrix; [cutoff], [min_clusters], [force_contiguous])
hc_partition_groups(Σ::Symmetric; [cutoff], [min_clusters], [force_contiguous])
```

Computes a group partition based on individual level data `X` or correlation  matrix `Σ` using hierarchical clustering with specified linkage. 

# Inputs

  * `X`: `n × p` data matrix. Each row is a sample
  * `Σ`: `p × p` correlation matrix. Must be wrapped in the `Symmetric` argument,   otherwise we will treat it as individual level data
  * `cutoff`: Height value for which the clustering result is cut, between 0 and 1   (default 0.5). This ensures that no variables between 2 groups have correlation   greater than `cutoff`. 1 recovers ungrouped structure, 0 corresponds to    everything in a single group.
  * `min_clusters`: The desired number of clusters.
  * `linkage`: *cluster linkage* function to use (when `force_contiguous=true`,    `linkage` must be `:single`). `linkage` defines how the    distances between the data points are aggregated into the distances between    the clusters. Naturally, it affects what clusters are merged on each    iteration. The valid choices are:

      * `:single` (default): use the minimum distance between any of the cluster members
      * `:average`: use the mean distance between any of the cluster members
      * `:complete`: use the maximum distance between any of the members
      * `:ward`: the distance is the increase of the average squared distance of a   point to its cluster centroid after merging the two clusters
      * `:ward_presquared`: same as `:ward`, but assumes that the distances in d    are already squared.
  * `rep_method`: Method for selecting representatives for each group. Options are   `:id` (tends to select roughly independent variables) or `:rss` (tends to   select more correlated variables)

If `force_contiguous = false` and both `min_clusters` and `cutoff` are specified,  it is guaranteed that the number of clusters is not less than `min_clusters` and their height is not above `cutoff`. If `force_contiguous = true`, `min_clusters` keyword is ignored. 

# Outputs

  * `groups`: Length `p` vector of group membership for each variable
  * `group_reps`: Columns of X selected as representatives. Each group have at    most `nrep` representatives. These are typically used to construct smaller   group knockoff for extremely large groups
