`struct RK_H3{T <: AbstractFloat} <: ReproducingKernel_3`

Define a type of reproducing kernel of Bessel Potential space $H^3_ε (R)$:

$$
V(\eta , \xi, \varepsilon) = \exp (-\varepsilon |\xi - \eta|)
             (3 + 3\varepsilon |\xi  - \eta| + \varepsilon ^2 |\xi - \eta| ^2 ) \, .
$$

# Arguments

  * no argument: means that parameter `ε` will be estimated in course of              interpolation procedure execution.
  * `ε::T`: 'scaling parameter' from the Bessel Potential space definition,          it must be greater than zero.
