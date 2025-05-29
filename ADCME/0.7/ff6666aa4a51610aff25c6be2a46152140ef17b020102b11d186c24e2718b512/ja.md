```
RBF3D(xc::Union{PyObject, Array{Float64, 1}}, yc::Union{PyObject, Array{Float64, 1}},
    zc::Union{PyObject, Array{Float64, 1}}; 
    c::Union{PyObject, Array{Float64, 1}, Missing} = missing, 
    eps::Union{PyObject, Array{Float64, 1}, Real, Missing} = missing,
    d::Union{PyObject, Array{Float64, 1}} = zeros(0), 
    kind::Int64 = 0)
```

3D領域上に放射基底関数の表現を構築します。

$$
f(x, y, z) = \sum_{i=1}^N c_i \phi(r; \epsilon_i) + d_0 + d_1 x + d_2 y + d_3 z
$$

ここで `d` は 0, 1（$d_0$ のみが存在）、または 4（$d_0$, $d_1$, $d_2$, および $d_3$ がすべて存在）である可能性があります。

`kind` は放射基底関数のタイプを決定します。

  * 0:ガウス

$$
\phi(r; \epsilon) = e^{-(\epsilon r)^2}
$$

  * 1:マルチクアドラティック

$$
\phi(r; \epsilon) = \sqrt{1+(\epsilon r)^2}
$$

  * 2:逆二次

$$
\phi(r; \epsilon) = \frac{1}{1+(\epsilon r)^2}
$$

  * 3:逆マルチクアドラティック

$$
\phi(r; \epsilon) = \frac{1}{\sqrt{1+(\epsilon r)^2}}
$$

呼び出し可能な構造体を返します。すなわち、位置 $(x, y, z)$ で関数を評価するには（`x`、`y`、および `z` はすべてベクトルです）、次のように実行します。

```julia
rbf(x, y, z)
```
