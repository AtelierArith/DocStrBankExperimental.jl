```
quadratic_expansion(A::IntervalMatrix, α::Real, β::Real)
```

Compute the quadratic expansion of an interval matrix, $αA + βA^2$, using interval arithmetic.

### Input

  * `A` – interval matrix
  * `α` – linear coefficient
  * `β` – quadratic coefficient

### Output

An interval matrix that encloses $B := αA + βA^2$.

### Algorithm

This a variation of the algorithm in [1, Section 6]. If $A = (aᵢⱼ)$ and $B := αA + βA^2 = (bᵢⱼ)$, the idea is to compute each $bᵢⱼ$ by factoring out repeated expressions (thus the term *single-use expressions*).

First, let $i = j$. In this case,

$$
bⱼⱼ = β\sum_\{k, k ≠ j} a_{jk} a_{kj} + (α + βa_{jj}) a_{jj}.
$$

Now consider $i ≠ j$. Then,

$$
bᵢⱼ = β\sum_\{k, k ≠ i, k ≠ j} a_{ik} a_{kj} + (α + βa_{ii} + βa_{jj}) a_{ij}.
$$

[1] Kosheleva, Kreinovich, Mayer, Nguyen. Computing the cube of an interval matrix is NP-hard. SAC 2005.
