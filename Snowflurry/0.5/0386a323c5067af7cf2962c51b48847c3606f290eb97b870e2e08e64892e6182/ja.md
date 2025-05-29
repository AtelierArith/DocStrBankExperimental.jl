```
rotation_y(theta)
```

$$
Y
$$

軸周りに角度`theta`の回転を適用する`Operator`を返します。

`Operator`は次のように定義されます：

$$
R_y(\theta) = \begin{bmatrix}
\mathrm{cos}\left(\frac{\theta}{2}\right) &
    -\mathrm{sin}\left(\frac{\theta}{2}\right) \\[0.5em]
\mathrm{sin}\left(\frac{\theta}{2}\right) &
    \mathrm{cos}\left(\frac{\theta}{2}\right)
\end{bmatrix}.
$$
