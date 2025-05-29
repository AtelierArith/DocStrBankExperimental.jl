`ψ(model::HarmonicOscillator, x; n::Int=0)`

$$
\psi_n(x) = A_n H_n(\xi) \exp{\left( -\frac{\xi^2}{2} \right)},
$$

where $\omega = \sqrt{k/m}$, $\xi = \sqrt{\frac{m\omega}{\hbar}}x$, $A_n = \sqrt{\frac{1}{n! 2^n} \sqrt{\frac{m\omega}{\pi\hbar}}}$, $H_n(x) = (-1)^n \mathrm{e}^{x^2} \frac{\mathrm{d}^n}{\mathrm{d}x^n} \mathrm{e}^{-x^2}$ are defined.
