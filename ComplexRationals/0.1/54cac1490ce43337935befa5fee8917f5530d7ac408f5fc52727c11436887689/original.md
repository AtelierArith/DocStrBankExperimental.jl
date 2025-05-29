```
is_negative(x::ComplexRational) -> Bool
```

Assuming `x` is given as (a + i·b)/c with c > 0 (as enforced by its constructor), this function returns true if the number should be printed with a negative sign.   The convention here is:

  * If the real part (a) is nonzero, return true if a < 0.
  * Otherwise (if a is zero), return true if the imaginary part (b) is negative.

If both are zero, returns false.
