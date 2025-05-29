```
Biquad(b0, b1, b2, a1, a2)
```

Filter representation in terms of the transfer function of a single second-order section given by:

$$
H(s) = \frac{\verb!b0! s^2+\verb!b1! s+\verb!b2!}{s^2+\verb!a1! s + \verb!a2!}
$$

or equivalently:

$$
H(z) = \frac{\verb!b0!+\verb!b1! z^{-1}+\verb!b2! z^{-2}}{1+\verb!a1! z^{-1} + \verb!a2! z^{-2}}
$$
