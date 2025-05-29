```
getmatrix()
```

Get the current workspace (position, scale, and orientation) as a 6-element vector:

```julia
[xx, yx, xy, yy, x0, y0]
```

  * `xx` component of the affine transformation
  * `yx` component of the affine transformation
  * `xy` component of the affine transformation
  * `yy` component of the affine transformation
  * `x0` translation component of the affine transformation
  * `y0` translation component of the affine transformation

When a drawing is first created, the 'matrix' looks like this:

```
getmatrix() = [1.0, 0.0, 0.0, 1.0, 0.0, 0.0]
```

When the origin is moved to 400/400, it looks like this:

```
getmatrix() = [1.0, 0.0, 0.0, 1.0, 400.0, 400.0]
```

To reset the 'matrix' to the original:

```
setmatrix([1.0, 0.0, 0.0, 1.0, 0.0, 0.0])
```

To modify the current 'matrix' by multiplying it by a 6 element 'matrix' `a`, see `transform(a::Array)`.

To convert between Luxor/Cairo 'matrix' format (6-element Vector{Float64}) and a 3x3 Julia matrix, use `cairotojuliamatrix(c)` and `juliatocairomatrix(c)`.

See also `rotationmatrix(a)`, `translationmatrix()`, and `scalingmatrix()`.

# Extended help

Here are some basic matrix transforms:

  * translate

    `transform([1, 0, 0, 1, dx, dy])` shifts by `dx`, `dy`
  * scale

    `transform([fx 0 0 fy 0 0])` scales by `fx` and `fy`
  * rotate

    `transform([cos(a), -sin(a), sin(a), cos(a), 0, 0])` rotates around to `a` radians

    rotate around O: [c -s s c 0 0]
  * shear

    `transform([1 0 a 1 0 0])` shears in x direction by `a`

    shear in y direction by `a`: `[1 a 0 1 0 0]`
  * x-skew

    `transform([1, 0, tan(a), 1, 0, 0])` skews in x by `a`
  * y-skew

    `transform([1, tan(a), 0, 1, 0, 0])` skews in y by `a`
  * flip

    `transform([fx, 0, 0, fy, centerx * (1 - fx), centery * (fy-1)])` flips with center at `centerx`/`centery`
  * reflect

    `transform([1 0 0 -1 0 0])` reflects in xaxis

    `transform([-1 0 0 1 0 0])` reflects in yaxis
