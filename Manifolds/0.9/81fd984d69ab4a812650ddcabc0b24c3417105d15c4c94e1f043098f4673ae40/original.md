```
project(M::AbstractSphere, p)
```

Project the point `p` from the embedding onto the [`Sphere`](@ref) `M`.

$$
\operatorname{proj}(p) = \frac{p}{\lVert p \rVert},
$$

where $\lVert⋅\rVert$ denotes the usual 2-norm for vectors if $m=1$ and the Frobenius norm for the case $m>1$.
