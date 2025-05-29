Implements the Bregman divergence, a friendly introduction to which can be found [here](http://mark.reid.name/blog/meet-the-bregman-divergences.html). Bregman divergences are a minimal implementation of the "mean-minimizer" property.

It is assumed that the (convex differentiable) function F maps vectors (of any type or size) to real numbers. The inner product used is `Base.dot`, but one can be passed in either by defining `inner` or by passing in a keyword argument. If an analytic gradient isn't available, Julia offers a suite of good automatic differentiation packages.

function evaluate(dist::Bregman, p::AbstractVector, q::AbstractVector)
