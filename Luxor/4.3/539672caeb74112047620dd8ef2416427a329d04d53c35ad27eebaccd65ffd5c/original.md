```
determinant3(p1::Point, p2::Point, p3::Point)
```

Find the determinant of the 3×3 matrix:

$$
\begin{bmatrix}
p1.x & p1.y & 1 \\
p2.x & p2.y & 1 \\
p3.x & p3.y & 1  \\
\end{bmatrix}
$$

If the value is 0.0, the points are collinear.
