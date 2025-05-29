`E(model::CoulombTwoBody; n::Int=1)`

$$
E_n
= -\frac{(z_1 z_2)^2}{2n^2} \frac{\mu}{m_\mathrm{e}} E_\mathrm{h},
$$

where $\mu=\left(\frac{1}{m_1}+\frac{1}{m_2}\right)^{-1}$ is the reduced mass of particle 1 and particle 2, $E_\mathrm{h} = \frac{\hbar^2}{m_\mathrm{e}{a_0}^2} = \frac{e^2}{4\pi\varepsilon_0a_0} = \frac{m_\mathrm{e}e^4}{\left(4\pi\varepsilon_0\right)^2\hbar^2}$ is the Hartree energy, one of atomic unit. About atomic units, see section 3.9.2 of the [IUPAC GreenBook](https://iupac.org/what-we-do/books/greenbook/). In other units, $E_\mathrm{h} = 27.211~386~245~988(53)~\mathrm{eV}$ from [here](https://physics.nist.gov/cgi-bin/cuu/Value?hrev).
