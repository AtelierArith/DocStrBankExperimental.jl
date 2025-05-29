```
savedataset(datasetpath, md; instance_ids, name, force = false)
```

Save `md` AbstractMultiDataset on disk at path `datasetpath` in the following format:

datasetpath     ├─ Example*1     │     └─ Modality*1.csv     │     └─ Modality*2.csv     │     └─ ...     │     └─ Modality*n.csv     │     └─ Metadata.txt     ├─ Example*2     │     └─ Modality*1.csv     │     └─ Modality*2.csv     │     └─ ...     │     └─ Modality*n.csv     │     └─ Metadata.txt     ├─ ...     ├─ Example_n     ├─ Metadata.txt     └─ Labels.csv

# Arguments

  * `instance_ids` is an `AbstractVector{Integer}` that denote the identifier of the instances,
  * `name` is an `AbstractString` and denote the name of the Dataset, that will be saved in the   Metadata of the Dataset,
  * `force` is a `Bool`, if it's set to `true`, then in case `datasetpath` already exists, it will   be overwritten otherwise the operation will be aborted. (default = `false`)
  * `labels_indices` is an `AbstractVector{Integer}` and contains the indices of the labels'   column (allowed only when passing a MultiDataset)

Alternatively to an `AbstractMultiDataset`, a `DataFrame` can be passed as second argument. If this is the case a third positional argument is required representing the `grouped_variables` of the dataset. See [`MultiDataset`](@ref) for syntax of `grouped_variables`.
