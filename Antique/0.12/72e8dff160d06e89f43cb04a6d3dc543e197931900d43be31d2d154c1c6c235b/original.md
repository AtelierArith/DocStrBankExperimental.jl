`ψ(model::MorsePotential, r; n::Int=0)`

$$
\psi_n(r) = N_n z^{\lambda-n-1/2} \mathrm{e}^{-z/2} L_n^{(2\lambda-2n-1)}(\xi),
$$

$N_n = \sqrt{\frac{n!(2\lambda-2n-1)a}{\Gamma(2\lambda-n)}}$, $\lambda = \frac{\sqrt{2\mu D_\mathrm{e}}}{a\hbar}$, $a = \sqrt{\frac{k}{2Dₑ}}$, $L_n^{(\alpha)}(x) = \frac{x^{-\alpha} \mathrm{e}^x}{n !} \frac{\mathrm{d}^n}{\mathrm{d} x^n}\left(\mathrm{e}^{-x} x^{n+\alpha}\right)$, $\xi := 2\lambda\mathrm{e}^{-a(r-r_e)}$ are defined. The domain is $0\leq r \lt \infty$.
