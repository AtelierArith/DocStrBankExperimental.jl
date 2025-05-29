```
project(x::AbstractVector, H::Hyperplane)
```

Project a point onto a hyperplane.

### Input

  * `x` – point
  * `H` – hyperplane

### Output

The projection of `x` onto `H`.

### Algorithm

The projection of $x$ onto the hyperplane of the form $a⋅x = b$ is

$$
    x - \dfrac{a (a⋅x - b)}{‖a‖²}
$$
