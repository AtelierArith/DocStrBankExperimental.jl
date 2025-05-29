```
box_approximation(ch::ConvexHull; [algorithm]::String="box")
```

Overapproximate a convex hull with a tight hyperrectangle.

### Input

  * `ch`        – convex hull
  * `algorithm` – (optional; default: `"box"`) algorithm choice

### Output

A hyperrectangle.

### Algorithm

Let `X` and `Y` be the two sets of `ch`. We make use of the following property:

$$
□(CH(X, Y))
    = □\left( X ∪ Y \right)
    = □\left( □(X) ∪ □(Y) \right)
$$

If `algorithm == "extrema"`, we compute the low and high coordinates of `X` and `Y` via `extrema`.

If `algorithm == "box"`, we instead compute the box approximations of `X` and `Y` via `box_approximation`.

In both cases we then take the box approximation of the result.

The `"extrema"` algorithm is more efficient if `extrema` is efficient because it does not need to allocate the intermediate hyperrectangles.
