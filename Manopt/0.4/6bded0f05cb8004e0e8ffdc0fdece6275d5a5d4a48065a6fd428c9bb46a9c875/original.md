```
WolfePowellLinesearch <: Linesearch
```

Do a backtracking line search to find a step size $α$ that fulfils the Wolfe conditions along a search direction $η$ starting from $x$ by

$$
f\bigl( \operatorname{retr}_x(αη) \bigr) ≤ f(x_k) + c_1 α_k ⟨\operatorname{grad}f(x), η⟩_x
\quad\text{and}\quad
\frac{\mathrm{d}}{\mathrm{d}t} f\bigr(\operatorname{retr}_x(tη)\bigr)
\Big\vert_{t=α}
≥ c_2 \frac{\mathrm{d}}{\mathrm{d}t} f\bigl(\operatorname{retr}_x(tη)\bigr)\Big\vert_{t=0}.
$$

# Constructors

There exist two constructors, where, when provided the manifold `M` as a first (optional) parameter, its default retraction and vector transport are the default. In this case the retraction and the vector transport are also keyword arguments for ease of use. The other constructor is kept for backward compatibility. Note that the `stop_when_stepsize_less` to stop for too small stepsizes is only available in the new signature including `M`.

```
WolfePowellLinesearch(M, c1::Float64=10^(-4), c2::Float64=0.999; kwargs...
```

Generate a Wolfe-Powell line search

## Keyword arguments

  * `candidate_point`:         (`allocate_result(M, rand)`) memory for a candidate
  * `candidate_tangent`:       (`allocate_result(M, zero_vector, candidate_point)`) memory for a gradient
  * `candidate_direcntion`:    (`allocate_result(M, zero_vector, candidate_point)`) memory for a direction
  * `max_stepsize`:            ([`max_stepsize`](@ref)`(M, p)`) largest stepsize allowed here.
  * `retraction_method`:       (`ExponentialRetraction()`) the retraction to use
  * `stop_when_stepsize_less`: (`0.0`) smallest stepsize when to stop (the last one before is taken)
  * `vector_transport_method`: (`ParallelTransport()`) the vector transport method to use
