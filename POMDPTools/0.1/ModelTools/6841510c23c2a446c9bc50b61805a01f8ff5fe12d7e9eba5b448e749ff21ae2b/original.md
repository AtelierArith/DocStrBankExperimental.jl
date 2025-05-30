```
ordered_observations(pomdp)
```

Return an `AbstractVector` of observations ordered according to `obsindex(pomdp, a)`.

`ordered_observations(mdp)` will always return a `AbstractVector{A}` `v` containing all of the observations in `observations(pomdp)` in the order such that `obsindex(pomdp, v[i]) == i`. You may wish to override this for your problem for efficiency.
