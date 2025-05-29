## Model

This model is described with the time-independent Schrödinger equation

$$
  \hat{H} \psi(x,y,z) = E \psi(x,y,z),
$$

and the Hamiltonian

$$
  \hat{H} = - \frac{\hbar^2}{2m} \left(\frac{\partial^2}{\partial x ^2} + \frac{\partial^2}{\partial y ^2} + \frac{\partial^2}{\partial z ^2}\right) + V(x,y,z).
$$

Parameters are specified with the following struct:

```
IPW3D = InfinitePotentialWell3D(L=[1.0,1.0,1.0], m=1.0, ℏ=1.0)
```

$L$ is a vector of the lengths of the box in $x$,$y$,$z$-direction, $m$ is the mass of particle and $\hbar$ is the reduced Planck constant (Dirac's constant).

## References

  * [D. A. McQuarrie, J. D. Simon, *Physical chemistry : a molecular approach* (University Science Books, 1997)](https://uscibooks.aip.org/books/physical-chemistry-a-molecular-approach/) p.90, 3-9. The Problem of a Particle in a Three-Dimensional Box Is a Simple Extension of the One-Dimensional Case
