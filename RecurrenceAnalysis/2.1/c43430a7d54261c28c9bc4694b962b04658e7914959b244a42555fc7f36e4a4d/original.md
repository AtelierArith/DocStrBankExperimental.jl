```
recurrencestructures(x::AbstractRecurrenceMatrix;
                         diagonal=true,
                         vertical=true,
                         recurrencetimes=true,
                         kwargs...)
```

Return a dictionary with the histograms of the recurrence structures contained in the recurrence matrix `x`, with the keys `"diagonal"`, `"vertical"` or `"recurrencetimes"`, depending on what keyword arguments are given as `true`.

## Description

Each item of the dictionary is a vector of integers, such that the `i`-th element of the vector is the number of lines of length `i` contained in `x`.

  * `"diagonal"` counts the diagonal lines, i.e. the recurrent trajectories.
  * `"vertical"` counts the vertical lines, i.e. the laminar states.
  * `"recurrencetimes"` counts the vertical distances between recurrent states,   i.e. the recurrence times.

All the points of the matrix are counted by default. The keyword argument `theiler` can be passed to rule out the lines around the main diagonal. See the arguments of the function [`rqa`](@ref) for further details.

"Empty" histograms are represented always as `[0]`.

*Notice*: There is not a unique operational definition of "recurrence times". In the analysis of recurrence plots, usually the  "second type" of recurrence times as defined by Gao and Cai [1] are considered, i.e. the distance between consecutive (but separated) recurrent structures in the vertical direction of the matrix. But that distance is not uniquely defined when the vertical recurrent structures are longer than one point. The recurrence times calculated here are the distance between the midpoints of consecutive lines, which is a balanced estimator of the Poincaré recurrence times [2].

## References

[1] J. Gao & H. Cai. "On the structures and quantification of recurrence plots". [*Physics Letters A*, 270(1-2), 75–87 (2000)](https://www.sciencedirect.com/science/article/pii/S0375960100003042?via%3Dihub).

[2] N. Marwan & C.L. Webber, "Mathematical and computational foundations of recurrence quantifications", in: Webber, C.L. & N. Marwan (eds.), *Recurrence Quantification Analysis. Theory and Best Practices*, Springer, pp. 3-43 (2015).
