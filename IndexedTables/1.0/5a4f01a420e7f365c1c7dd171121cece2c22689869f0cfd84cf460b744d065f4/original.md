`convertdim(x::NDSparse, d::DimName, xlate; agg::Function, vecagg::Function, name)`

Apply function or dictionary `xlate` to each index in the specified dimension. If the mapping is many-to-one, `agg` or `vecagg` is used to aggregate the results. If `agg` is passed, it is used as a 2-argument reduction function over the data. If `vecagg` is passed, it is used as a vector-to-scalar function to aggregate the data. `name` optionally specifies a new name for the translated dimension.
