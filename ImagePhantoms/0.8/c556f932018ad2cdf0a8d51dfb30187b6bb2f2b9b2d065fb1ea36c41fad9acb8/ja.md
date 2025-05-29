```
gauss2(cx, cy, wx, wy=wx, ϕ=0, value::Number=1)
gauss2(center::NTuple{2,RealU}, width::NTuple{2,RealU}=(1,1), ϕ::RealU=0, v=1)
gauss2(w, v=1) (幅 `w` の等方性)

パラメータから `Object{Gauss2}` を構築します。ここで `width` = FWHM（半値全幅）です。

1Dの場合、式は `g(x) = exp(-π ((x - cx) / sx)^2)` であり、ここで `sx = fwhm2spread(w) = w * sqrt(π / log(16))` です。`cx=0` の場合、1D FT は `G(ν) = sx^2 exp(π (sx νx)^2)` となります。
```
