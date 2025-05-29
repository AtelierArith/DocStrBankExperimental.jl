`struct RK_H2{T <: AbstractFloat} <: ReproducingKernel_2`

Defines a type of reproducing kernel of Bessel Potential space $H^{n/2 + 5/2}_ε (R^n)$ ('Quadratic Matérn kernel'):

$$
V(\eta , \xi, \varepsilon) = \exp (-\varepsilon |\xi - \eta|)
             (3 + 3\varepsilon |\xi  - \eta| + \varepsilon ^2 |\xi - \eta| ^2 ) \, .
$$

# Fields

  * `ε::T`: 'scaling parameter' from the Bessel Potential space definition,          it may be omitted in the struct constructor otherwise it must be greater than zero
