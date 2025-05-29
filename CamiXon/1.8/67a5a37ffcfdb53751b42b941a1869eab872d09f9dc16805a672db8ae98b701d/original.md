```
getNmin(f::Vector{T}, start::Int, stop:Int) where T<:Real
getNmin(f::Vector{T}, itr::UnitRange) where T<:Real
```

Index corresponding to the absolute minimum of the discrete function $f[n]$ truncated  at the boundary of the interval $start ≤ n ≤ stop$.  Condition: $f'[n]$ must be monotonically increasing or decreasing on the interval ${start,stop}$.

NB. For a regular parabola the algorithm finds the index of the minimum. A truncated inverted parabola has  two minima (at the boundaries of the interval). In this case the algorithm finds the index  of the lowest of the two. If undecided the result is start.
