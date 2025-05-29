```
rotation_x(theta)
```

$$
X
$$

軸周りの回転`theta`を適用する`Operator`を返します。

`Operator`は次のように定義されます：

$$
R_x(\theta) = \begin{bmatrix}
\mathrm{cos}\left(\frac{\theta}{2}\right) &
    -i\mathrm{sin}\left(\frac{\theta}{2}\right) \\[0.5em]
-i\mathrm{sin}\left(\frac{\theta}{2}\right) &
    \mathrm{cos}\left(\frac{\theta}{2}\right)
\end{bmatrix}.
$$
