```
getrotation(R::Matrix)
getrotation()
```

Juliaの3x3行列の回転、または現在のLuxorの回転を取得します。

```julia-repl
julia> getrotation()
0.0
```

$$
\begin{bmatrix}
a & b & tx \\
c & d & ty \\
0 & 0 & 1  \\
\end{bmatrix}
$$

回転角は`atan(-b, a)`または`atan(c, d)`です。

詳細については`getmatrix()`を参照してください。
