```
rotation(theta, phi)
```

回転 `theta` を軸 :\vec{n}=\cos(\phi)~X+\sin(\phi)~Y} に関して適用する `Operator` を返します。

`Operator` は次のように定義されます：

$$
R(\theta, \phi) = \begin{bmatrix}
    \mathrm{cos}\left(\frac{\theta}{2}\right) &
        -i e^{-i\phi} \mathrm{sin}\left(\frac{\theta}{2}\right) \\[0.5em]
    -i e^{i\phi} \mathrm{sin}\left(\frac{\theta}{2}\right) &
        \mathrm{cos}\left(\frac{\theta}{2}\right)
\end{bmatrix}.
$$
