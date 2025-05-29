```
SkewNormal(ξ, ω, α)
```

The *skew normal distribution* is a continuous probability distribution that generalises the normal distribution to allow for non-zero skewness. Given a location `ξ`, scale `ω`, and shape `α`, it has the probability density function

$$
f(x; \xi, \omega, \alpha) =
\frac{2}{\omega \sqrt{2 \pi}} \exp{\bigg(-\frac{(x-\xi)^2}{2\omega^2}\bigg)}
\int_{-\infty}^{\alpha\left(\frac{x-\xi}{\omega}\right)}
\frac{1}{\sqrt{2 \pi}}  \exp{\bigg(-\frac{t^2}{2}\bigg)} \, \mathrm{d}t
$$

External links

  * [Skew normal distribution on Wikipedia](https://en.wikipedia.org/wiki/Skew_normal_distribution)
  * [Discourse](https://discourse.julialang.org/t/skew-normal-distribution/21549/7)
  * [SkewDist.jl](https://github.com/STOR-i/SkewDist.jl)
