```
corners = corner2subpixel(responses::AbstractMatrix,corner_indicator::AbstractMatrix{Bool})
        -> Vector{HomogeneousPoint{Float64,3}}
```

Refines integer corner coordinates to sub-pixel precision. The function takes as input a matrix representing corner responses and a boolean indicator matrix denoting the integer coordinates of a corner in the image. The output is a vector of type [`HomogeneousPoint`](@ref) storing the sub-pixel coordinates of the corners. The algorithm computes a correction factor which is added to the original integer coordinates. In particular, a univariate quadratic polynomial is fit separately to the $x$-coordinates and $y$-coordinates of a corner and its immediate east/west, and north/south neighbours. The fit is achieved using a local coordinate system for each corner, where the origin of the coordinate system is a given corner, and its immediate neighbours are assigned coordinates of  minus one and plus one. The corner and its two neighbours form a system of three equations. For example, let  $x_1 = -1$,  $x_2 = 0$ and  $x_3 = 1$ denote the local $x$ coordinates of the west, center and east pixels and let the vector $\mathbf{b} = [r_1, r_2, r_3]$ denote the corresponding corner response values. With

$$
    \mathbf{A} =
        \begin{bmatrix}
            x_1^2 & x_1  & 1  \\
            x_2^2 & x_2  & 1 \\
            x_3^2 & x_3  & 1 \\
        \end{bmatrix},
$$

the coefficients of the quadratic polynomial can be found by solving the system of equations $\mathbf{b} = \mathbf{A}\mathbf{x}$. The result is given by $x = \mathbf{A}^{-1}\mathbf{b}$. The vertex of the quadratic polynomial yields a sub-pixel estimate of the true corner position. For example, for a univariate quadratic polynomial $px^2 + qx + r$, the $x$-coordinate of the vertex is $\frac{-q}{2p}$. Hence, the refined sub-pixel coordinate is equal to:  $c +  \frac{-q}{2p}$, where $c$ is the integer coordinate.

!!! note
    Corners on the boundary of the image are not refined to sub-pixel precision.

