Constant to use when specifying the Euclidean or L2 distance metric for a sequencing run. This sets the default threshold to the value of [`L2THR`](@ref) = 1e-7.

To set a different threshold level, use the type constructor `Distances.Euclidean(<your value>)` directly (i.e. instead of the `L2` constant).
