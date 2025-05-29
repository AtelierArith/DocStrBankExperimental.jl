```
beziercurvature(t, A::Point, A1::Point, B1::Point, B::Point)
```

Return the curvature of the Bézier curve at `t` in [0, 1], given start and end points A and B, and control points A1 and B1. The value (kappa) will typically be a value between -0.001 and 0.001 for points with coordinates in the 100-500 range.

$κ(t)$ is the curvature of the curve at point t, which for a parametric planar curve is:

$$
\begin{equation}
κ = \frac{\left| ẋ ÿ - ẏ ẍ \right|}{(ẋ^2 + ẏ^2)^{\frac{3}{2}}}
\end{equation}
$$

The radius of curvature, or the radius of an osculating circle at a point, is 1/κ(t). Values of 1/κ will typically be in the range -1000 to 1000 for points with coordinates in the 100-500 range.

TODO Fix overshoot...

...The value of kappa can sometimes collapse near 0, returning NaN (and Inf for radius of curvature).
