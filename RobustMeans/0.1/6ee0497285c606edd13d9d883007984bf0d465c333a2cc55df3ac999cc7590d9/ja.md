```
SmoothingKernel
```

  * `h` はバンド幅パラメータです。
  * `f` はカーネル関数です。

カーネルの例は次のとおりですが（独自のものを定義することもできます）

```julia
uniform(u::T) where T<:Real = abs(u) > one(T) ? zero(T) : 1 / 2
epanechnikov(u::T) where T<:Real = abs(u) > one(T) ? zero(T) : 3 / 4 * (1 - u^2)
gaussian(u::T) where T<:Real = abs(u) > one(T) ? zero(T) : (1 / sqrt(2 * pi)) * exp(-1 / 2 * u^2)
triangular(u::T) where T<:Real = abs(u) > one(T) ? zero(T) : (1 - abs(u))
biweight(u::T) where T<:Real = abs(u) > one(T) ? zero(T) : 15 / 16 * (1 - u^2)^2
triweight(u::T) where T<:Real = abs(u) > one(T) ? zero(T) : 35 / 32 * (1 - u^2)^3
tricube(u::T) where T<:Real = abs(u) > one(T) ? zero(T) : 70 / 81 * (1 - abs(u)^3)^3
cosine(u::T) where T<:Real = abs(u) > one(T) ? zero(T) : (pi / 4) * cos((pi / 2) * u)
logistic(u::T) where T<:Real = abs(u) > one(T) ? zero(T) : 1 / (exp(u) + 2 + exp(-u))
```
