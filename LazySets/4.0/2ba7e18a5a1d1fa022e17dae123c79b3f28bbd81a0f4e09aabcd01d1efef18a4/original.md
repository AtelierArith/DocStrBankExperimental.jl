```
Rectification{N, S<:LazySet{N}} <: LazySet{N}
```

Type that represents the rectification of a set.

### Fields

  * `X`     – set
  * `cache` – storage of information computed before

### Notes

Given a vector $v = (v_1, …, v_n)$, its rectification is defined as $\text{rectify}(v) = (v_1', …, v_n')$ such that $v_i' = \max(v_i, 0)$ for each $i = 1, …, n$.

The extension to a set $X$ is defined elementwise:

$$
    \text{rectify}(X) = \{\text{rectify}(x) \mid x ∈ X\}
$$

The rectification of a convex set $X$ is not necessarily convex.

It can be expressed exactly as the union of the intersection of $X$ with the nonnegative orthant and the projection of the intersection of $X$ with each other orthant. This can be seen as follows.

First we observe that rectification distributes with union.

$$
    \text{rectify}(X_1 ∪ … ∪ X_m) = ⋃_j \text{rectify}(X_j)
$$

Next we express $X$ as the union of the intersection of $X$ with each orthant $O$.

$$
    X = ⋃_j (X ∩ O_j)
$$

Thus we have

$$
    \text{rectify}(X) = \text{rectify}((X ∩ O_1) ∪ … ∪ (X ∩ O_m)) = ⋃_j \text{rectify}(X ∩ O_j).
$$

Clearly, $\text{rectify}(X ∩ O_j) = X$ if $O_j$ is the nonnegative orthant.

For example, consider a two-dimensional case and call the orthants $O_1, …, O_4$ in clockwise fashion, starting with the nonnegative orthant. We conclude that

$$
    \text{rectify}(X) = (X ∩ O_1) ∪ \text{rectify}(X ∩ O_2) ∪ \text{rectify}(X ∩ O_3) ∪ \text{rectify}(X ∩ O_4).
$$

The rectification of the intersection in the nonpositive orthant, $\text{rectify}(X ∩ O_3)$, is either the empty set or the singleton containing the origin. The rectification of $X ∩ O_2$ and $X ∩ O_4$ both result in flat $1$-dimensional line segments on the corresponding hyperplane of $O_1$.
