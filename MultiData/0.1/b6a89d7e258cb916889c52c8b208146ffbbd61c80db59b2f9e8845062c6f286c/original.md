Abstract supertype for all multimodal datasets.

A concrete multimodal dataset should always provide accessors [`data`](@ref), to access the underlying tabular structure (e.g., `DataFrame`) and [`grouped_variables`](@ref), to access the grouping of variables (a vector of vectors of column indices).
