```
SineWindow(offset, endpoint, power, tmax)
```

Abstract window function representing multiplication by sine/cosine functions. Acquisition time is `tmax`.

$$
\left[\sin\left(
    \pi\cdot\mathrm{offset} +
    \frac{\left(\mathrm{end} - \mathrm{offset}\right)\pi t}{\mathrm{tmax}}
    \right)\right]^\mathrm{power}
$$

Specialises to `CosWindow`, `Cos²Window` or `GeneralSineWindow`.

# Arguments

  * `offset`: initial value is $\sin(\mathrm{offset}\cdot\pi)$ (0 to 1)
  * `endpoint`: initial value is $\sin(\mathrm{endpoint}\cdot\pi)$ (0 to 1)
  * `pow`: sine exponent
