```
# compute the zeros, poles, and k-factor of a transfer function
z, p, k = zeros_poles_k(tf)
# construct a transfer function from its zeros, poles, and k-factor
tf = zeros_poles_k(z, p, k, time_delay=0.0)
```

the representation of a transfer function in this context is:

$$
g(s)=k\dfrac{\Pi_j (s-z_j)}{\Pi_j (s-p_j)}
$$

where $z_j$ is zero $j$, $p_j$ is pole $j$, and $k$ is a constant factor (not equal to the zero-frequency gain) that uniquely specifies the transfer function.

  * the zeros are the zeros of the numerator of the transfer function.
  * the poles are the zeros of the denominator of the transfer function.
