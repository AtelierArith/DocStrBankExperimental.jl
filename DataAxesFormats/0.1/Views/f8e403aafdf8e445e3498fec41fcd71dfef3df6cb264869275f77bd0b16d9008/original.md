Specify an axis to expose from a view.

This is specified as a vector of pairs (similar to initializing a `Dict`). The order of the pairs matter (last one wins). We also allow specifying tuples instead of pairs to make it easy to invoke the API from other languages such as Python which do not have the concept of a `Pair`.

If the key is `"*"`, then it is replaced by all the names of the axes of the wrapped `daf` data. Otherwise, the key is just the name of an axis.

If the value is `nothing`, then the axis will **not** be exposed by the view. If the value is `"="`, then the axis will be exposed with the same entries as in the original `daf` data. Otherwise the value is any valid query that returns a vector of (unique!) strings to serve as the vector entries.

That is, specifying `"*"` (or, [`ALL_AXES`](@ref) will expose all the original `daf` data axes from the view. Following this by saying `"type" => nothing` will hide the `type` from the view. Saying `"batch" => q"/ batch & age > 1` will expose the `batch` axis, but only including the batches whose `age` property is greater than 1.
