TaylorFourierTransform.ftft(s::Vector{<:Number}, t::Vector{<:Number}, D::Int, F::Real, K::Int)

Input:

  * `s::Vector{<:Number}` | discrete signal [?]
  * `t::Vector{<:Number}` | discrete time [s]
  * `D::Int`              | maximum degree of the derivatives [-]
  * `F::Real`             | fundamental frequency [Hz]
  * `K::Int`              | degree of the o-spline [-]

Output:

  * `sol::DTFTSolution`   | DTFT solution struct
