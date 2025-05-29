```
σ(d::AbstractVector, R::Rectification{N, <:AbstractHyperrectangle}) where {N}
```

Return a support vector of the rectification of a hyperrectangular set.

### Input

  * `d` – direction
  * `R` – rectification of a hyperrectangular set

### Output

A support vector in the given direction.

### Algorithm

Let $R(·)$ be the rectification of a vector respectively a set, and let $H$ be a hyperrectangle. Then $σ_{R(H)}(d) = R(σ_{H}(d))$.
