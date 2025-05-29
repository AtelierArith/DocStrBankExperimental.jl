`struct RK_H2{T <: AbstractFloat} <: ReproducingKernel_2`

Define a type of reproducing kernel of Bessel Potential space $H^2_ε (R)$:

$$
V(\eta , \xi, \varepsilon) = \exp (-\varepsilon |\xi - \eta|)
             (1 + \varepsilon |\xi  - \eta|) \, .
$$

# Arguments

  * no argument: means that parameter `ε` will be estimated in course of              interpolation procedure execution.
  * `ε::T`: 'scaling parameter' from the Bessel Potential space definition,          it must be greater than zero.
