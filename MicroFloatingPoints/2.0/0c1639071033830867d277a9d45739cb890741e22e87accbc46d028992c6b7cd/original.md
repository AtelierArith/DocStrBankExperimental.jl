```
fractional_even(x::Floatmu{szE,szf}) where {szE,szf}
```

Return `true` if the fractional part of `x` has a zero as the rightmost bit.

BEWARE: the function does not check whether `x` is an NaN or an infinite value.
