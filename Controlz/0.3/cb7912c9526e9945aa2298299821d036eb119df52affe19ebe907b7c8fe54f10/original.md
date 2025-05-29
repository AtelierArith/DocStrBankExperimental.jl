```
tf = zpk_form(tf)
```

write transfer function `tf` in zeros, poles, k-factor form:

$$
g(s)=k\dfrac{\Pi_j (s-z_j)}{\Pi_j (s-p_j)}
$$

where $z_j$ is zero $j$, $p_j$ is pole $j$, and $k$ is a constant factor (not equal to the zero-frequency gain) that uniquely specifies the transfer function.

this is achieved by multiplying by 1.0 in a fancy way such that the highest power of $s$ in the denominator is associated with a coefficient of $1$.

# Example

```jldoctest
g = 8.0 / (2 * s^2 + 3 * s + 4)
g_zpk = zpk_form(g)
# output
         4.0
---------------------
1.0*s^2 + 1.5*s + 2.0
```
