```
reflect(x::AbstractVector, H::Hyperplane)
```

Reflect (mirror) a vector in a hyperplane.

### Input

  * `x` – point/vector
  * `H` – hyperplane

### Output

The reflection of `x` in `H`.

### Algorithm

The reflection of a point $x$ in the hyperplane $a ⋅ x = b$ is

$$
    x − 2 \frac{x ⋅ a − b}{a ⋅ a} a
$$

where $u · v$ denotes the dot product.
