```
getNmax(f::Vector{T}, start::Int, stop:Int) where T<:Real
getNmax(f::Vector{T}, itr::UnitRange) where T<:Real
```

Index corresponding to the absolute maximum of the discrete function $f[n]$ truncated  at the boundaries of the interval $start ≤ n ≤ stop$.  Condition: $f'[n]$ must be monotonically increasing or decreasing on the interval ${start,stop}$.

NB. For an inverted parabola the algorithm finds the index of the extremum. A regular parabola  has two maxima (at the boundaries of the search interval). In this case the algorithm finds the  index of the highest of the two. If undecided the result is start.
