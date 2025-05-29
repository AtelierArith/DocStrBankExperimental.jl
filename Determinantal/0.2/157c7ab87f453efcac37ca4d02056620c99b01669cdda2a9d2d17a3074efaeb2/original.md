```
distance_sampling(x,m,sampling)

Select a random subset of size m from x based on a greedy distance criterion. The initial point is selected uniformly. Then, if sampling == :farthest, at each step, the point selected is one that is farthest from all currently selected points. If sampling == :d2, the algorithm is D²-sampling [vassilvitskii2006k](@vassilvitskii2006k), which is a relaxed stochastic version of farthest-point sampling (selecting points with prob. proportional to squared distance).
```

```@example
x = rand(2, 200);
ind = distance_sampling(ColVecs(x), 40, :farthest)
scatter(x[1, :], x[2, :]; marker_z=map((v) -> v ∈ ind, 1:size(x, 2)), legend=:none)
```
