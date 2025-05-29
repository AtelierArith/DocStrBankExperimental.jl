```
get_circle_info(hs::AbstractArray, c::AbstractArray; rattol::Number=1e-8,
                ratcutoff::Number=1e-4, max_island_d::Integer=30)
```

Get a Fourier representation of an invariant circle from the observations `hs` and the learned filter `c` (see `adaptive_invariant_circle_model` and `invariant_circle_model` to find the filter). See `get_circle_residual` for an a posteriori validation of the circle.

Optional Arguments:

  * `rattol`: Roots are judged to be rational if |ω-m/n|<rattol
  * `ratcutoff`: Relative prominence needed by a linear mode to qualify as "important" for deciding whether the sequence is an island
  * `max_island_d`: Maximum denominator considered for islands.
  * `modetol`: Tolerance (typically less than 1) used for determining the number of Fourier modes. Higher numbers result in more Fourier modes at the expense of robustness of the least-squares system.  Decrease it (e.g. to 0.5) for noisy data

Output:

  * `z`: An invariant circle of type `FourierCircle`
