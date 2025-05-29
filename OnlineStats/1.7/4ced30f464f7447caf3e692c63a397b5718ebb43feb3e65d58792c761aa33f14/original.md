```
Hist(edges; left = true, closed = true)
```

Create a histogram with bin partition defined by `edges`.

  * If `left`, the bins will be left-closed.
  * If `closed`, the bin on the end will be closed.

      * E.g. for a two bin histogram $[a, b), [b, c)$ vs. $[a, b), [b, c]$

# Example

```
o = fit!(Hist(-5:.1:5), randn(10^6))

# approximate statistics
using Statistics

mean(o)
var(o)
std(o)
quantile(o)
median(o)
extrema(o)
```
