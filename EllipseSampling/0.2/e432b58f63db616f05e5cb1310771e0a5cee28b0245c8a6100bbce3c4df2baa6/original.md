```
construct_ellipse(x_radius::T, y_radius::T, α::T=0.0, Cx::T=0.0, Cy::T=0.0) where T<:Float64
```

Constructs a [`EllipseSampling.Ellipse`](@ref) `struct` which contains the information required to define an ellipse which may have been rotated and translated.

# Arguments

  * `x_radius`: radius of the ellipse in the x axis (i.e. when the rotation, `α`, is zero).
  * `y_radius`: radius of the ellipse in the y axis (i.e. when the rotation, `α`, is zero).
  * `α`: an angle in radians (0 to 2π) that the ellipse has been rotated by. A positive value represents an anti-clockwise rotation. Default is `0.0`.
  * `Cx`: the x coordinate of the centre of the ellipse (the translation of the ellipse in the x axis). Default is `0.0`.
  * `Cy`: the y coordinate of the centre of the ellipse (the translation of the ellipse in the y axis). Default is `0.0`.

# Details

The general equation for a rotated and translated ellipse is given by:

$$
1 = A(x-C_x)^2 + B(x-C_x)(y-C_y) + C(y-C_y)^2
$$

Where:

$$
A = \bigg(\frac{\cos^2(α)}{a^2} + \frac{\sin^2(α)}{b^2}\bigg)
$$

$$
B = 2\cos(α)\sin(α)\bigg(\frac{1}{a^2} - \frac{1}{b^2}\bigg)
$$

$$
C = \bigg(\frac{\sin^2(α)}{a^2} + \frac{\cos^2(α)}{b^2}\bigg)
$$
