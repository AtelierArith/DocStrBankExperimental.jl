```
overapproximate(X::ConvexHull{N, <:AbstractZonotope, <:AbstractZonotope},
                ::Type{<:Zonotope}) where {N}
```

Overapproximate the convex hull of two zonotopic sets.

### Input

  * `X`         – convex hull of two zonotopic sets
  * `Zonotope`  – target set type
  * `algorithm` – (optional; default: `"mean"`) choice of algorithm; possible                values are `"mean"` and `"join"`

### Output

A zonotope $Z$ such that $X ⊆ Z$.

### Algorithm

The algorithm can be controlled by the parameter `algorithm`. Note that the results of the two implemented algorithms are generally incomparable.

##### 'mean' method

If `algorithm == "mean"`, we choose the method proposed in [Girard05](@citet). The convex hull of two zonotopic sets $Z₁$ and $Z₂$ of the same order, which we write

$$
Z_j = ⟨c^{(j)}, g^{(j)}_1, …, g^{(j)}_p⟩
$$

for $j = 1, 2$, can be overapproximated as follows:

$$
CH(Z_1, Z_2) ⊆ \frac{1}{2}⟨c^{(1)}+c^{(2)}, g^{(1)}_1+g^{(2)}_1, …,
g^{(1)}_p+g^{(2)}_p, c^{(1)}-c^{(2)}, g^{(1)}_1-g^{(2)}_1, …, g^{(1)}_p-g^{(2)}_p⟩.
$$

If the zonotope order is not the same, this algorithm calls `reduce_order` to reduce the order to the minimum of the arguments.

It should be noted that the output zonotope is not necessarily the minimal enclosing zonotope, which is in general expensive to obtain in high dimensions. This is further investigated in [GuibasNZ03](@citet).

##### 'join' method

If `algorithm == "join"`, we choose the method proposed in [GhorbalGP09; Definition 1](@citet). The convex hull $X$ of two zonotopic sets $Z₁$ and $Z₂$ is overapproximated by a zonotope $Z₃$ such that the box approximation of $X$ is identical with the box approximation of $Z₃$. Let $□(X)$ denote the box approximation of $X$. The center of $Z₃$ is the center of $□(X)$.

The generator construction consists of two phases. In the first phase, we construct generators $g$ as a combination of one generator from $Z₁$, say, $g₁$, with another generator from $Z₂$, say, $g₂$. The entry of $g$ in the $i$-th dimension is given as

$$
    g[i] = \argmin_{\min(g₁[i], g₂[i]) ≤ x ≤ \max(g₁[i], g₂[i])} |x|.
$$

If $g$ is the zero vector, it can be omitted.

In the second phase, we construct another generator for each dimension. These generators are scaled unit vectors. The following formula defines the sum of all those generators.

$$
    \sup(□(X)) - c - ∑_g |g|
$$

where $c$ is the center of the new zonotope and the $g$s are the generators constructed in the first phase.
