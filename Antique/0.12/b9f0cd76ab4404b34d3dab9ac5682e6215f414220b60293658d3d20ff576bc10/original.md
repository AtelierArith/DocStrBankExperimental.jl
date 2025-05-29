`ψ(model::PoschlTeller, x; n::Int=0)`

$$
\psi_n(x) = \frac{(-1)^μ}{\sqrt{x_0}} P_\lambda^{\mu}(\mathrm{tanh}(x/x_0)) \sqrt{\mu\frac{\Gamma(\lambda-\mu+1)}{\Gamma(\lambda+\mu+1)}},
$$

where $\mu = \mu(n) = n_\mathrm{max}-n+1$, and $n_\mathrm{max} = \left\lfloor \lambda \right\rfloor - 1$ and $P_\lambda^{\mu}$ are the associated Legendre functions.
