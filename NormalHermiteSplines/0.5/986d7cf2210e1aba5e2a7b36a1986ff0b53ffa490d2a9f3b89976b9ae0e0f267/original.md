`struct RK_H0{T <: AbstractFloat} <: ReproducingKernel_0`

Defines a type of reproducing kernel of Bessel Potential space $H^{n/2 + 1/2}_ε (R^n)$ ('Basic Matérn kernel'):

$$
V(\eta , \xi, \varepsilon) = \exp (-\varepsilon |\xi - \eta|) \, .
$$

# Fields

  * `ε::T`: 'scaling parameter' from the Bessel Potential space definition,          it may be omitted in the struct constructor otherwise it must be greater than zero
