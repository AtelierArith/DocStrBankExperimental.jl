`struct RK_H1{T <: AbstractFloat} <: ReproducingKernel_1`

Defines a type of reproducing kernel of Bessel Potential space $H^{n/2 + 3/2}_ε (R^n)$ ('Linear Matérn kernel'):

$$
V(\eta , \xi, \varepsilon) = \exp (-\varepsilon |\xi - \eta|)
             (1 + \varepsilon |\xi  - \eta|) \, .
$$

# Fields

  * `ε::T`: 'scaling parameter' from the Bessel Potential space definition,          it may be omitted in the struct constructor otherwise it must be greater than zero
