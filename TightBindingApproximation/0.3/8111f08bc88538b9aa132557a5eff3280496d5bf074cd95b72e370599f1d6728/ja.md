```
Kubo{K<:Union{Nothing, Vector{Float64}}} <: BerryCurvatureMethod
```

占有エネルギーバンドの総ベリー曲率を計算するためのクーボ法。クーボ公式は次のように与えられます。

$$
\Omega_{ij}(\bm k)=\epsilon_{ijl}\sum_{n}f(\epsilon_n(\bm k))b_n^l(\bm k)=-2{\rm Im}\sum_v\sum_c{V_{vc,i}(\bm k)V_{cv,j}(\bm k)\over [\omega_c(\bm k)-\omega_v(\bm k)]^2},
$$

ここで

$$
 V_{cv,j}={\langle u_{c\bm k}|{\partial H\over \partial {\bm k}_j}|u_{v\bm k}\rangle}
$$

vおよびcの添え字は、それぞれ価電子（占有）バンドと伝導（非占有）バンドを示します。2D空間におけるホール伝導率は次のように与えられます。

$$
\sigma_{xy}=-{e^2\over h}\int_{BZ}{dk_x dk_y\over 2\pi}{\Omega_{xy}}
$$
