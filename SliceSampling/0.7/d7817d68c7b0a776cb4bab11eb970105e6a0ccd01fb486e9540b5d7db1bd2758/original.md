```
GibbsPolarSlice(w; max_proposals)
```

Gibbsian polar slice sampling algorithm by P. Schär, M. Habeck, and D. Rudolf [^SHR2023].

# Arguments

  * `w::Real`: Initial window size for the radius shrinkage procedure.

# Keyword Arguments

  * `w::Real`: Initial window size for the radius shrinkage procedure
  * `max_proposals::Int`: Maximum number of proposals allowed until throwing an error (default: `10000`).

!!! info
    By the nature of polar coordinates, GPSS only works reliably for targets with dimension at least $d \geq 2$.


!!! info
    The initial window size `w` must be set at least an order of magnitude larger than what is sensible for other slice samplers. Otherwise, a large number of rejections might be experienced.


!!! warning
    When initializing the chain (*e.g.* the `initial_params` keyword arguments in `AbstractMCMC.sample`), it is necessary to inialize from a point $x_0$ that has a sensible norm $\lVert x_0 \rVert > 0$, otherwise, the chain will start from a pathologic point in polar coordinates. This might even result in the sampler getting stuck in an infinite loop. (This can be prevented by setting `max_proposals`.) If $\lVert x_0 \rVert \leq 10^{-5}$, the current implementation will display a warning.


!!! info
    For Turing users: `Turing` might change `initial_params` to match the support of the posterior. This might lead to $\lVert x_0 \rVert$ being small, even though the vector you passed to`initial_params` has a sufficiently large norm. If this is suspected, simply try a different initialization value.

