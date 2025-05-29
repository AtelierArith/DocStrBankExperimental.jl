```
χₚ(s)
chi_p(s)
```

Effective precession spin parameter of the system.

Note that there are *two different* definitions of this quantity found in the literature. The [original definition](https://arxiv.org/abs/1408.1810) (converted to the convention where $M_1 \geq M_2$) is

$$
\begin{gathered}
A_1 = 2 + \frac{3M_2}{2M_1} \\
A_2 = 2 + \frac{3M_1}{2M_2} \\
\chi_{\mathrm{p}} \colonequals \frac{1}{A_1 M_1^2}
\mathrm{max}\left(A_1 S_{1\perp}, A_2 S_{2\perp} \right).
\end{gathered}
$$

In a paper from early in the detection era, the [LIGO collaboration used this definition](https://arxiv.org/abs/1606.01210).

However, a [more recent paper](https://arxiv.org/abs/2010.04131) redefines this essentially as $M_1^2$ times that quantity.  Using the convention that $q = M_2/M_1 \leq 1$, the definition may be more compactly written as

$$
\chi_{\mathrm{p}} \colonequals \mathrm{max} \left(
    \chi_{1\perp}, \chi_{2\perp} q \frac{4q+3}{4+3q}
\right).
$$

Again, a more recent paper by [LIGO/Virgo/KAGRA](https://arxiv.org/abs/2111.03606) uses this convention.

Because it seems to be the trend, this function uses the latter definition.
