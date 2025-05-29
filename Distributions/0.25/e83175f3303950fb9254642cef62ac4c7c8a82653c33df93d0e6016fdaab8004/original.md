```
TriangularDist(a,b,c)
```

The *triangular distribution* with lower limit `a`, upper limit `b` and mode `c` has probability density function

$$
f(x; a, b, c)= \begin{cases}
        0 & \mathrm{for\ } x < a, \\
        \frac{2(x-a)}{(b-a)(c-a)} & \mathrm{for\ } a \le x \leq c, \\[4pt]
        \frac{2(b-x)}{(b-a)(b-c)} & \mathrm{for\ } c < x \le b, \\[4pt]
        0 & \mathrm{for\ } b < x,
        \end{cases}
$$

```julia
TriangularDist(a, b)        # Triangular distribution with lower limit a, upper limit b, and mode (a+b)/2
TriangularDist(a, b, c)     # Triangular distribution with lower limit a, upper limit b, and mode c

params(d)       # Get the parameters, i.e. (a, b, c)
minimum(d)      # Get the lower bound, i.e. a
maximum(d)      # Get the upper bound, i.e. b
mode(d)         # Get the mode, i.e. c
```

External links

  * [Triangular distribution on Wikipedia](http://en.wikipedia.org/wiki/Triangular_distribution)
