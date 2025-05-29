```
Arcsine(a,b)
```

The *Arcsine distribution* has probability density function

$$
f(x) = \frac{1}{\pi \sqrt{(x - a) (b - x)}}, \quad x \in [a, b]
$$

```julia
Arcsine()        # Arcsine distribution with support [0, 1]
Arcsine(b)       # Arcsine distribution with support [0, b]
Arcsine(a, b)    # Arcsine distribution with support [a, b]

params(d)        # Get the parameters, i.e. (a, b)
minimum(d)       # Get the lower bound, i.e. a
maximum(d)       # Get the upper bound, i.e. b
location(d)      # Get the left bound, i.e. a
scale(d)         # Get the span of the support, i.e. b - a
```

External links

  * [Arcsine distribution on Wikipedia](http://en.wikipedia.org/wiki/Arcsine_distribution)

Use `Arcsine(a, b, check_args=false)` to bypass argument checks.
