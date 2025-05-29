Abstract supertype for all labeled multimodal datasets (used in supervised learning).

As any multimodal dataset, any concrete labeled multimodal dataset should always provide the accessors [`data`](@ref), to access the underlying tabular structure (e.g., `DataFrame`) and [`grouped_variables`](@ref), to access the grouping of variables. In addition to these, implementations are required for [`labeling_variables`](@ref), to access the indices of the labeling variables.

See also [`AbstractMultiDataset`](@ref).
