```
madv(x)
```

Compute the median absolute deviation (MAD) of a vector. 

  * `x` : A vector (n).

This is the MAD adjusted by a factor (1.4826) for asymptotically  normal consistency.

## Examples

```julia
using Jchemo

x = rand(100)
madv(x)
```
