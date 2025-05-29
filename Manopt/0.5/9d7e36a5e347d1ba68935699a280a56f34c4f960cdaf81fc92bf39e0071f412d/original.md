```
WolfePowellLinesearch(; kwargs...)
WolfePowellLinesearch(M::AbstractManifold; kwargs...)
```

Perform a lineseach to fulfull both the Armijo-Goldstein conditions

$$
f\bigl( \operatorname{retr}_{p}(αX) \bigr) ≤ f(p) + c_1 α_k ⟨\operatorname{grad} f(p), X⟩_{p}
$$

as well as the Wolfe conditions

$$
\frac{\mathrm{d}}{\mathrm{d}t} f\bigl(\operatorname{retr}_{p}(tX)\bigr)
\Big\vert_{t=α}
≥ c_2 \frac{\mathrm{d}}{\mathrm{d}t} f\bigl(\operatorname{retr}_{p}(tX)\bigr)\Big\vert_{t=0}.
$$

for some given sufficient decrease coefficient $c_1$ and some sufficient curvature condition coefficient$c_2$.

This is adopted from [NocedalWright:2006; Section 3.1](@cite)

# Keyword arguments

  * `sufficient_decrease=10^(-4)`
  * `sufficient_curvature=0.999`
  * `p::P`: a point on the manifold $\mathcal M$as temporary storage for candidates
  * `X::T`: a tangent vector at the point $p$ on the manifold $\mathcal M$as type of memory allocated for the candidates direction and tangent
  * `max_stepsize=`[`max_stepsize`](@ref)`(M, p)`: largest stepsize allowed here.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stop_when_stepsize_less=0.0`: smallest stepsize when to stop (the last one before is taken)
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
