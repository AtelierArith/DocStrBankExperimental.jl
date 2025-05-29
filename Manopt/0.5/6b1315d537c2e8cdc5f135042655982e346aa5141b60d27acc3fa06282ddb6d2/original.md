```
WolfePowellBinaryLinesearch(; kwargs...)
WolfePowellBinaryLinesearch(M::AbstractManifold; kwargs...)
```

Perform a lineseach to fulfull both the Armijo-Goldstein conditions for some given sufficient decrease coefficient $c_1$ and some sufficient curvature condition coefficient$c_2$. Compared to [`WolfePowellLinesearch`](@ref Manopt.WolfePowellLinesearch) which tries a simpler method, this linesearch performs the following algorithm

With

$$
A(t) = f(p_+) ≤ c_1 t ⟨\operatorname{grad}f(p), X⟩_{x}
\quad\text{ and }\quad
W(t) = ⟨\operatorname{grad}f(x_+), \mathcal T_{p_+←p}X⟩_{p_+} ≥ c_2 ⟨X, \operatorname{grad}f(x)⟩_x,
$$

where $p_+ =\operatorname{retr}_p(tX)$ is the current trial point, and $\mathcal T_{⋅←⋅}$ denotes a vector transport. Then the following Algorithm is performed similar to Algorithm 7 from [Huang:2014](@cite)

1. set $α=0$, $β=∞$ and $t=1$.
2. While either $A(t)$ does not hold or $W(t)$ does not hold do steps 3-5.
3. If $A(t)$ fails, set $β=t$.
4. If $A(t)$ holds but $W(t)$ fails, set $α=t$.
5. If $β<∞$ set $t=\frac{α+β}{2}$, otherwise set $t=2α$.

# Keyword arguments

  * `sufficient_decrease=10^(-4)`
  * `sufficient_curvature=0.999`
  * `max_stepsize=`[`max_stepsize`](@ref)`(M, p)`: largest stepsize allowed here.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stop_when_stepsize_less=0.0`: smallest stepsize when to stop (the last one before is taken)
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
