```
qnm_schw_expansion_dolan_ottewill(::Type{TF}, s::TI, l::TI, n::TI) where {TF<:AbstractFloat,TI<:Integer}
```

Compute the high $\ell$ asymptotic expansion of Schwarzschild QNM frequency, using the method of Dolan and Ottewill [Dolan:2009nk](@cite).

The QNM frequency can be written as an expansion in inverse powers of $L=\ell+\frac{1}{2}$

$$
\omega_{l n}=\varpi_{-1}^{(n)} L+\varpi_0^{(n)}+\varpi_1^{(n)} L^{-1}+\varpi_2^{(n)} L^{-2}+\ldots
$$

The lowest expansion coefficients for arbitrary spin $\beta=1-s^2$ and arbitrary overtone number $n$ are given by

$$
\begin{aligned}
& \sqrt{27} \varpi_{-1}^{(n)}=1 \\
& \sqrt{27} \varpi_0^{(n)}=-i N \\
& \sqrt{27} \varpi_1^{(n)}=\frac{\beta}{3}-\frac{5 N^2}{36}-\frac{115}{432} \\
& \sqrt{27} \varpi_2^{(n)}=-i N\left[\frac{\beta}{9}+\frac{235 N^2}{3888}-\frac{1415}{15552}\right] \\
& \sqrt{27} \varpi_3^{(n)}=-\frac{\beta^2}{27}+\frac{204 N^2+211}{3888} \beta+\frac{854160 N^4-1664760 N^2-776939}{40310784} \\
& \sqrt{27} \varpi_4^{(n)}=i N\left[\frac{\beta^2}{27}+\frac{1100 N^2-2719}{46656} \beta+\frac{11273136 N^4-52753800 N^2+66480535}{2902376448}\right]
\end{aligned}
$$

# Arguments

  * `TF`: Type of the floating-point number.
  * `s`: Spin weight of the field of interest.
  * `l`: Multipole number of interest.
  * `n`: Overtone number of interest.

# References

  * [Dolan:2009nk](@cite)
  * [qnm/qnm/schwarzschild/approx.py at master · duetosymmetry/qnm](https://github.com/duetosymmetry/qnm/blob/master/qnm/schwarzschild/approx.py)
