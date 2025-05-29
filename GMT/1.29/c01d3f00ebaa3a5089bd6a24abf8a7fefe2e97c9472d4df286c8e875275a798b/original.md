```
FV = torus(; r=2.0, R=5.0, center=(0.0, 0.0, 0.0), nx=100, ny=50) -> GMTfv
```

Create a torus mesh with radius `r`. 

### Kwargs

  * `r`: the inner radius of the torus.
  * `R`: the outer radius of the torus.
  * `center`: A 3-element array or tuple of three numbers defining the origin of the body. Default is `(0.0, 0.0, 0.0)`.
  * `nx`: the number of vertices in the xx direction.
  * `ny`: the number of vertices in the yy direction.
