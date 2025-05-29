```
nnuq(H::Array{Float64,2}, invR::Union{Float64, Array{Float64,2}}, invQ::Union{Float64, Array{Float64,2}})
```

ベイズ逆行列の分散行列を返します。

負の対数尤度関数は次のようになります。

$$
l(s) =\frac{1}{2} (y-h(s))^T R^{-1} (y-h(s)) + \frac{1}{2} s^T Q^{-1} s
$$

共分散行列はまず$h(s)$を線形化することによって計算されます。

$$
h(s)\approx h(s_0) + \nabla h(s_0) (s-s_0)
$$

その後、二次導関数を計算します。

$$
V = \left(\frac{\partial^2 l}{\partial s^T\partial s}\right)^{-1} = (H^T R^{-1} H + Q^{-1})^{-1}
$$

結果は$s_0$、$y_0$に依存せず、$\nabla h(s_0)$のみに依存することに注意してください。
