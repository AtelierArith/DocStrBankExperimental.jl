## Model

This model is described with the time-independent Schrödinger equation

$$
  \hat{H} \psi(\theta,\varphi) = E \psi(\theta,\varphi),
$$

and the Hamiltonian

$$
\begin{aligned}
  \hat{H} &= - \frac{\hbar^2}{2\mu} \nabla^2 + V(r), \\
          &= - \frac{\hbar^2}{2I} \left[ \frac{1}{\sin\theta} \frac{\partial}{\partial\theta} \left(\sin\theta \frac{\partial}{\partial\theta}\right) + \frac{1}{\sin^2\theta} \frac{\partial^2}{\partial\phi^2}  \right], \\
          &= \frac{L^2}{2I}
\end{aligned}
$$

where $I=\mu R^2$ is the moment of intertia, $\mu=\left(\frac{1}{m_1}+\frac{1}{m_2}\right)^{-1}$ is the reduced mass of two particles, $R$ is the distance between the two particles, and $L^2$ is the angular momentum operator. Parameters are specified with the following struct:

```
RR = RigidRotor(m₁=1.0, m₂=1.0, R=1.0, ℏ=1.0)
```

$m₁$ and $m₂$ are mass of two particles, $R$ is the distance, and $\hbar$ is the reduced Planck constant (Dirac's constant).

## References

  * [D. A. McQuarrie, J. D. Simon, *Physical chemistry : a molecular approach* (University Science Books, 1997)](https://uscibooks.aip.org/books/physical-chemistry-a-molecular-approach/) p.173, 5.8 The Energy Levels of a Rigid Rotator Are $E = \hbar^2 J(J+1) / 2I$
  * [Chemistry Libre Texts](https://chem.libretexts.org/Bookshelves/Physical_and_Theoretical_Chemistry_Textbook_Maps/Physical_Chemistry_(LibreTexts)/05%3A_The_Harmonic_Oscillator_and_the_Rigid_Rotor/5.08%3A_The_Energy_Levels_of_a_Rigid_Rotor)
