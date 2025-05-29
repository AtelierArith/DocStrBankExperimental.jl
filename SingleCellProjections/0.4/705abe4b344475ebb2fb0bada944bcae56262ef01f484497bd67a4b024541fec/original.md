```
project(data::DataMatrix, base::DataMatrix, args...; from=nothing, kwargs...)
```

Project `data` onto `base`, by applying ProjectionModels from `base` one by one.

Since `data` already might have some models applied, `project` will try to figure out which models from `base` to use. See "Examples" below for concrete examples. Here's a more technical overview:

Consider a `base` data matrix with four models:

```
base: A -> B -> C -> D
```

Given some new `data` (typically counts), we can project that onto `base`, given the result `proj` by applying all four models:

```
data:
proj: A -> B -> C -> D
```

If `data` already has some models applied (e.g. we already projected onto A and B above), `project` will look for the last model in `data` (in this case B) in the list of models in `base`, and only apply models after that (in this case C and D).

```
data: A -> B
proj: A -> B -> C -> D
```

It is also possible to use the `from` kwarg to specify exactly which models to apply. (The models in `from` must be a prefix of the models in `base`, or in other words, `base` was created by applying additional operations to `from`.)

```
data: X
base: A -> B -> C -> D
from: A -> B
proj: X -> C -> D
```

Note that it is necessary to use the `from` kwarg if the last model in `data` does not occurr in `base`, because `project` cannot figure out on its own which models it makes sense to apply.

# Examples

First, we construct a "base" by loading counts, SCTransforming, normalizing, computing the svd and finally computing a force layout:

```julia
julia> fp = ["GSE164378_RNA_ADT_3P_P1.h5", "GSE164378_RNA_ADT_3P_P2.h5"];
julia> counts = load_counts(fp; sample_names=["P1","P2"]);
julia> transformed = sctransform(counts);
julia> normalized = normalize_matrix(transformed);
julia> reduced = svd(normalized; nsv=10);
julia> fl = force_layout(reduced; ndim=3, k=100)
  DataMatrix (3 variables and 35340 observations)
  Matrix{Float64}
  Variables: id
  Observations: id, sampleName, barcode
  Models: NearestNeighborModel(base="force_layout", k=10), SVD, Normalization, SCTransform
```

Note how the last line lists all `ProjectionModels` used in the creation of `fl`.

Next, let's load some more samples for projection:

```julia
julia> fp2 = ["GSE164378_RNA_ADT_3P_P5.h5", "GSE164378_RNA_ADT_3P_P6.h5"];
julia> counts2 = load_counts(fp2; sample_names=["P5","P6"]);
```

It is easy to project the newly loaded `counts2` onto the "base" force layout `fl`:

```julia
julia> project(counts2, fl)
DataMatrix (3 variables and 42553 observations)
  Matrix{Float64}
  Variables: id
  Observations: id, sampleName, barcode
  Models: NearestNeighborModel(base="force_layout", k=10), SVD, Normalization, SCTransform
```

We can also project in two or more steps, to get access to intermediate results:

```julia
julia> reduced2 = project(counts2, reduced)
DataMatrix (20239 variables and 42553 observations)
  SVD (10 dimensions)
  Variables: id, feature_type, name, genome, read, pattern, sequence, logGeneMean, outlier, beta0, ...
  Observations: id, sampleName, barcode
  Models: SVDModel(nsv=10), Normalization, SCTransform

julia> project(reduced2, fl)
DataMatrix (3 variables and 42553 observations)
  Matrix{Float64}
  Variables: id
  Observations: id, sampleName, barcode
  Models: NearestNeighborModel(base="force_layout", k=10), SVD, Normalization, SCTransform
```

If the DataMatrix we want to project is modified, we need to use the `from` kwarg to tell `project` which models to use:

```julia
julia> filtered = counts2[:,1:10:end]
DataMatrix (33766 variables and 4256 observations)
  SparseArrays.SparseMatrixCSC{Int64, Int32}
  Variables: id, feature_type, name, genome, read, pattern, sequence
  Observations: id, sampleName, barcode
  Models: FilterModel(:, 1:10:42551)

julia> reduced2b = project(filtered2, reduced; from=counts)
DataMatrix (20239 variables and 4256 observations)
  SVD (10 dimensions)
  Variables: id, feature_type, name, genome, read, pattern, sequence, logGeneMean, outlier, beta0, ...
  Observations: id, sampleName, barcode
  Models: SVDModel(nsv=10), Normalization, SCTransform, Filter
```

After that, it is possible to continue without specifying `from`:

```julia
julia> project(reduced2b, fl)
DataMatrix (3 variables and 4256 observations)
  Matrix{Float64}
  Variables: id
  Observations: id, sampleName, barcode
  Models: NearestNeighborModel(base="force_layout", k=10), SVD, Normalization, SCTransform, Filter
```
