```
ShallowWaterTwoLayerEquations1D(gravity, H0, rho_upper, rho_lower)
```

Two-Layer Shallow Water equations (2LSWE) in one space dimension. The equations are given by

$$
\begin{alignat*}{4}
&\frac{\partial}{\partial t}h_{upper}
&&+ \frac{\partial}{\partial x}\left(h_{upper} v_{1,upper}\right)
&&= 0 \\
&\frac{\partial}{\partial t}\left(h_{upper}v_{1,upper}\right)
&&+ \frac{\partial}{\partial x}\left(h_{upper}v_{1,upper}^2 + \dfrac{gh_{upper}^2}{2}\right)
&&= -gh_{upper}\frac{\partial}{\partial x}\left(b+h_{lower}\right)\\
&\frac{\partial}{\partial t}h_{lower}
&&+ \frac{\partial}{\partial x}\left(h_{lower}v_{1,lower}\right)
&&= 0 \\
&\frac{\partial}{\partial t}\left(h_{lower}v_{1,lower}\right)
&&+ \frac{\partial}{\partial x}\left(h_{lower}v_{1,lower}^2 + \dfrac{gh_{lower}^2}{2}\right)
&&= -gh_{lower}\frac{\partial}{\partial x}\left(b+\dfrac{\rho_{upper}}{\rho_{lower}}h_{upper}\right).
\end{alignat*}
$$

The unknown quantities of the 2LSWE are the water heights of the {lower} layer $h_{lower}$ and the {upper} layer $h_{upper}$ with respective velocities $v_{1,upper}$ and $v_{1,lower}$. The gravitational acceleration is denoted by `g`, the layer densitites by $\rho_{upper}$and $\rho_{lower}$ and the (possibly) variable bottom topography function $b(x)$. The conservative variable water height $h_{lower}$ is measured from the bottom topography $b$ and $h_{upper}$ relative to $h_{lower}$, therefore one also defines the total water heights as $H_{upper} = h_{upper} + h_{upper} + b$ and $H_{lower} = h_{lower} + b$.

The densities must be chosen such that $\rho_{upper} < \rho_{lower}$, to make sure that the heavier fluid $\rho_{lower}$ is in the bottom layer and the lighter fluid $\rho_{upper}$ in the {upper} layer.

The additional quantity $H_0$ is also available to store a reference value for the total water height that is useful to set initial conditions or test the "lake-at-rest" well-balancedness.

The bottom topography function $b(x)$ is set inside the initial condition routine for a particular problem setup.

In addition to the unknowns, Trixi currently stores the bottom topography values at the approximation points despite being fixed in time. This is done for convenience of computing the bottom topography gradients on the fly during the approximation as well as computing auxiliary quantities like the total water height $H$ or the entropy variables. This affects the implementation and use of these equations in various ways:

  * The flux values corresponding to the bottom topography must be zero.
  * The bottom topography values must be included when defining initial conditions, boundary conditions or source terms.
  * [`Trixi.AnalysisCallback`](@extref) analyzes this variable.
  * Trixi's visualization tools will visualize the bottom topography by default.

A good introduction for the 2LSWE is available in Chapter 12 of the book:

  * Benoit Cushman-Roisin (2011)
    Introduction to geophyiscal fluid dynamics: physical and numerical aspects
    [https://www.sciencedirect.com/bookseries/international-geophysics/vol/101/suppl/C](https://www.sciencedirect.com/bookseries/international-geophysics/vol/101/suppl/C)
    ISBN: 978-0-12-088759-0
