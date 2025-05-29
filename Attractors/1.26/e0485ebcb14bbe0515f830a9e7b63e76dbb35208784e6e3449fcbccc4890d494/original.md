```
GroupViaPairwiseComparison <: GroupingConfig
GroupViaPairwiseComparison(; threshold::Real, metric...)
```

Initialize a struct that contains instructions on how to group features in [`AttractorsViaFeaturizing`](@ref). `GroupViaPairwiseComparison` groups features and identifies clusters by considering the pairwise distance between features. It can be used as an alternative to the clustering method in `GroupViaClustering`, having the advantage that it is simpler, typically faster and uses less memory.

## Keyword arguments

  * `threshold = 0.1`: A real number defining the maximum distance two features can have to be considered in the same cluster - above the threshold, features are different. This value simply needs to be large enough to differentiate clusters. A good value for `threshold` depends on the feature variability within a cluster the chosen metric, and whether features are rescaled. See description below for more.
  * `metric = Euclidean()`: A function `metric(a, b)` that returns the distance between two features `a` and `b`, outputs of `featurizer`. Any `Metric` from Distances.jl can be used here.
  * `rescale_features = true`: if true, rescale each dimension of the extracted features separately into the range `[0, 1]`. This typically leads to more accurate grouping for the default `metric. threshold`, however, it should be avoid for when there is only one attractor for the system, because it leads to it being wrongly classified as many different attractors at the same location).

## Description

This algorithm assumes that the features are well-separated into distinct clouds, with the maximum radius of the cloud controlled by `threshold`. Since the systems are deterministic, this is achievable with a good-enough `featurizer` function, by removing transients, and running the trajectories for sufficiently long. It then considers that features belong to the same attractor when their pairwise distance, computed using `metric`, is smaller than or equal to `threshold`, and that they belong to different attractors when the distance is bigger. Attractors correspond to each grouping of similar features. In this way, the key parameter `threshold` is basically the amount of variation permissible in the features belonging to the same attractor. If they are well-chosen, the value can be relatively small and does not need to be fine tuned.

The `threshold` should achieve a balance: one one hand, it should be large enough to account for variations in the features from the same attractor - if it's not large enough, the algorithm will find duplicate attractors. On the other hand, it should be small enough to not group together features from distinct attractors. This requires some knowledge of how spread the features are. If it's too big, the algorithm will miss some attractors, as it groups 2+ distinct attractors together. Therefore, as a rule of thumb, one can repeat the procedure a few times, starting with a relatively large value and reducing it until no more attractors are found and no duplicates appear.

The method scales as O(N) in memory and performance with N the number of features. This is a huge difference versus the O(N^2) of [`GroupViaClustering`](@ref).
