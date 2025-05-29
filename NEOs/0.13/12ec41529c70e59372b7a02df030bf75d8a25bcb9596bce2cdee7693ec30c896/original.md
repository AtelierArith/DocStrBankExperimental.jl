```
yarkp2adot(A2, a, e, μ_S)
```

Return the average semimajor axis drift due to the Yarkovsky effect

$$
\begin{align*}
    \left\langle\dot{a}\right\rangle & = \frac{2A_2(1-e^2)}{n}\left(\frac{1 \ \text{AU}}{p}\right)^2 \\
    & = \frac{2A_2}{(1-e^2)\sqrt{a\mu_\odot}}(1 \ \text{AU})^2,
\end{align*}
$$

where $A_2$ is the Yarkovsky parameter, $\mu_\odot = GM_\odot$ is the Sun's gravitational parameter, $e$ is the eccentricity, $n = \sqrt{\mu/a^3}$ is the mean motion, $p = a(1-e^2)$ is the semilatus rectum, and $a$ is the semimajor axis.

# Arguments

  * `A2`: Yarkovsky parameter.
  * `a`: semimajor axis.
  * `e`: eccentricity.
  * `μ_S`: mass parameter of the Sun.

!!! reference
    See https://doi.org/10.1016/j.icarus.2013.02.004.

