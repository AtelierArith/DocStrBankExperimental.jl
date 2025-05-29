```
PeriodicEuclidean(L)
```

Create a Euclidean metric on a rectangular periodic domain (i.e., a torus or a cylinder). Periods per dimension are contained in the vector `L`:

$$
\sqrt{\sum_i(\min\mod(|x_i - y_i|, p), p - \mod(|x_i - y_i|, p))^2}.
$$

For dimensions without periodicity put `Inf` in the respective component.

# Example

```jldoctest
julia> x, y, L = [0.0, 0.0], [0.75, 0.0], [0.5, Inf];

julia> evaluate(PeriodicEuclidean(L), x, y)
0.25
```
