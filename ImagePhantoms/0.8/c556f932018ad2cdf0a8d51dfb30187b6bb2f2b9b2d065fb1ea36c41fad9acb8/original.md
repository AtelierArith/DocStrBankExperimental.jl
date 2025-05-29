```
gauss2(cx, cy, wx, wy=wx, ϕ=0, value::Number=1)
gauss2(center::NTuple{2,RealU}, width::NTuple{2,RealU}=(1,1), ϕ::RealU=0, v=1)
gauss2(w, v=1) (isotropic of width `w`)
```

Construct `Object{Gauss2}` from parameters; here `width` = FWHM (full-width at half-maximum).

In 1D, the formula is `g(x) = exp(-π ((x - cx) / sx)^2)` where `sx = fwhm2spread(w) = w * sqrt(π / log(16))`, which, for `cx=0`,  has 1D FT `G(ν) = sx^2 exp(π (sx νx)^2)`.
