`FastBandlimited(s1, s2, fun, bandlimit;                 quadn_add=default_extra_quad(s1),                 roughpoints=nothing)`

A constructor for a `FastBandlimited` object that represents the action of a matrix `M` with entries `M[j,k] = g(s1[j] - s2[k])` with `g` satisfying

$ g(t) = ∫_{[-bandlimit, bandlimit]^{dim}} e^{-2 π i t^T ω} fun(ω) d ω $

for `t` and `Ω` in R^{dim}. Arguments are:

  * `s1::Union{Vector{Float64}, Vector{SVector{D,Float64}}` with `1 <= D <= 3`.
  * `s2::Union{Vector{Float64}, Vector{SVector{D,Float64}}` with `1 <= D <= 3`.
  * `bandlimit::Union{Float64, [iterable]{D,Float64}}`. If you pass in points in multiple dimensions and bandlimit is a `Float64`, that will be interpreted to mean that the bandlimit in every dimension is the same.

Keyword arguments are:

  * `quadn_add=default_extra_quad(s1)`. the number of quadrature nodes beyond Nyquist to add in each dimension. So in 1D you can make this 1000 without breaking a sweat. But if you make it 1000 in 3D, you're adding 10^9 nodes!  So be careful. You hopefully won't have to touch this argument so long as you provide roughpoints correctly.
  * `roughpoints::Union{Nothing, [iterable]{D,Float64}}=nothing`. This argument  is the way that you communicate locations at which `fun` is not smooth. If you don't do this, the quadrature rule will be much less accurate. This kwarg should just be an iterable of frequencies that match the dimension and type of your location. See the example file of the fast sinc squared transform for an example of telling `FastBandlimited` that the 2D triangular function is rough  at the origin. This is an important arg to get right! And there is no easy way for the code to catch it if you forget–-you'll just silently get wrong answers.
