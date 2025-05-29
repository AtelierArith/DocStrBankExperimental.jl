`struct RK_H1{T <: AbstractFloat} <: ReproducingKernel_1`

Define a type of reproducing kernel of Bessel Potential space $H^1_ε (R)$:

$$
V(\eta , \xi, \varepsilon) = \exp (-\varepsilon |\xi - \eta|) \, .
$$

# Arguments

  * no argument: means that parameter `ε` will be estimated in course of              interpolation procedure execution.
  * `ε::T`: 'scaling parameter' from the Bessel Potential space definition,          it must be greater than zero.
