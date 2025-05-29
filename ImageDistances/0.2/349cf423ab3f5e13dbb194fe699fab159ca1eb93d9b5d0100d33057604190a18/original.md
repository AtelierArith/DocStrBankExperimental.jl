```
ModifiedHausdorff <: GenericHausdorff
modified_hausdorff(x::BoolImage, y::BoolImage)
```

Modified Hausdorff distance between two point sets $\mathcal{A}$ and $\mathcal{B}$, which consist of point positions of 1s of `x` and `y`, respectively. The distance is computed using the following formula:

$$
    \text{modified_hausdorff}(x,y) = max(d(\mathcal{A}, \mathcal{B}), d(\mathcal{B}, \mathcal{A}))
$$

where

$$
    d(\mathcal{A}, \mathcal{B}) = \frac{1}{N_a}\sum_{a\in\mathcal{A}}d(a, \mathcal{B}) \\
    d(a, \mathcal{B}) = max_{b\in\mathcal{B}}d(a, b)
$$

and the point distance is calcuated using [`Euclidean`](@ref) distance.

## References

Dubuisson, M-P; Jain, A. K., 1994. *A Modified Hausdorff Distance for Object-Matching*.

See also: [`hausdorff`](@ref)
