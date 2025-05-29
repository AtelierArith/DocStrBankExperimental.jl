```
Semicircle(r)
```

The Wigner semicircle distribution with radius parameter `r` has probability density function

$$
f(x; r) = \frac{2}{\pi r^2} \sqrt{r^2 - x^2}, \quad x \in [-r, r].
$$

```julia
Semicircle(r)   # Wigner semicircle distribution with radius r

params(d)       # Get the radius parameter, i.e. (r,)
```

External links

  * [Wigner semicircle distribution on Wikipedia](https://en.wikipedia.org/wiki/Wigner_semicircle_distribution)
