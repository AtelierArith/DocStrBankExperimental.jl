```
z, p, gain = zeros_poles_gain(tf)
```

Compute the zeros, poles, and zero-frequency gain of a transfer function.

  * the zeros are the zeros of the numerator of the transfer function.
  * the poles are the zeros of the denominator of the transfer function.
  * the zero-frequency gain is the transfer function evaluated at $s=0$
