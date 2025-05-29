```
tan_rev(c::Interval[, x::Interval])
```

Reverse tangent. Calculates the preimage of `a = tan(x)`. If `x` is not provided, then byt default $[-∞, ∞]$ is used. See section 10.5.4 of the IEEE 1788-2015 standard for interval arithmetic.

### Output

The pair `(c, x_new)` where

  * `c` is unchanged
  * `x_new` is the interval hull of the set ${x ∈ b : tan(x) ∈ a}$
