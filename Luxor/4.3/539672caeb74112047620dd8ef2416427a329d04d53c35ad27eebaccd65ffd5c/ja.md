```
determinant3(p1::Point, p2::Point, p3::Point)
```

3×3行列の行列式を求めます：

$$
\begin{bmatrix}
p1.x & p1.y & 1 \\
p2.x & p2.y & 1 \\
p3.x & p3.y & 1  \\
\end{bmatrix}
$$

値が0.0の場合、点は共線です。
