Specify a single datum to expose from view. This is specified as a vector of pairs (similar to initializing a `Dict`). The order of the pairs matter (last one wins). We also allow specifying tuples instead of pairs to make it easy to invoke the API from other languages such as Python which do not have the concept of a `Pair`.

**Scalars** are specified similarly to [`ViewAxes`](@ref), except that the query should return a scalar instead of a vector. That is, saying `"*"` (or [`ALL_SCALARS`](@ref)) will expose all the original `daf` data scalars from the view. Following this by saying `"version" => nothing` will hide the `version` from the view. Adding `"total_umis" => q"/ cell / gene : UMIs %> Sum %> Sum"` will expose a `total_umis` scalar containing the total sum of all UMIs of all genes in all cells, etc.

**Vectors** are specified similarly to scalars, but require a key specifying both an axis and a property name. The axis must be exposed by the view (based on the `axes` parameter). If the axis is `"*"`, it is replaces by all the exposed axis names specified by the `axes` parameter. Similarly, if the property name is `"*"` (e.g., `("gene", "*")`), then  it is replaced by all the vector properties of the exposed axis in the base data. Therefore specifying `("*", "*")` (or [`ALL_VECTORS`](@ref))`, all vector properties of all the (exposed) axes will also be exposed.

The value for vectors must be the suffix of a vector query based on the appropriate axis; a value of `"="` is again used to expose the property as-is.

For example, specifying `axes = ["cell" => q"/ cell & type = TCell"]`, and then `data = [("cell", "total_noisy_UMIs") => q"/ gene & noisy : UMIs %> Sum` will expose `total_noisy_UMIs` as a per-`cell` vector property, using the query `/ gene & noisy / cell & type = TCell : UMIs %> Sum`, which will compute the sum of the `UMIs` of all the noisy genes for each cell (whose `type` is `TCell`).

**Matrices** require a key specifying both axes and a property name. The axes must both be exposed by the view (based on the `axes` parameter). Again if any or both of the axes are `"*"`, they are replaced by all the exposed axes (based on the `axes` parameter), and likewise if the name is `"*"`, it replaced by all the matrix properties of the axes. The value for matrices can again be `"="` to expose the property as is, or the suffix of a matrix query. Therefore specifying `("*", "*", "*")` (or, `ALL_MATRICES`), all matrix properties of all the (exposed) axes will also be exposed.

That is, assuming a `gene` and `cell` axes were exposed by the `axes` parameter, then specifying that `("cell", "gene", "log_UMIs") => q": UMIs % Log base 2 eps"` will expose the matrix `log_UMIs` for each cell and gene.

The order of the axes does not matter, so `data = [("gene", "cell", "UMIs") => "="]` has the same effect as `data = [("cell", "gene", "UMIs") => "="]`.

**3D Tensors** require a key specifying the main axis, followed by two axes, and a property name. All the axes must be exposed by the view (based on the `axes` parameter). In this cases, none of the axes may be `"*"`. The value can only be be `"="` to expose all the matrix properties of the tensor as they are or `nothing` to hide all of them; that is, views can expose or hide existing (possibly masked) 3D tensors, but can't be used to create new ones.

That is, assuming a `gene`, `cell` and `batch` axes were exposed by the `axes` parameters, then specifying that `("batch", "cell", "gene", "is_measured") => "="` will expose the set of per-cell-per-gene matrices `batch1_is_measured`, `batch2_is_measured`, etc.
