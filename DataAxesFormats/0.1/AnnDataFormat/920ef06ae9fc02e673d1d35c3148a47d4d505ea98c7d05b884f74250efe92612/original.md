Import/export `Daf` data from/to [AnnData](https://pypi.org/project/anndata/). We use the `AnnData` Julia implementation from [Muon.jl](https://github.com/scverse/Muon.jl).

Due to the different data models, not all the content of `AnnData` can be represented as `Daf`, and vice-versa. However, "most" of the data can be automatically converted from one form to the other. In both directions, conversion is zero-copy; that is, we merely create a different view for the same vectors and matrices. We also use memory-mapping whenever possible for increased performance.

The following `Daf` data can't be naively stored in `AnnData`:

  * `AnnData` is restricted to storing data for only two axes, which `AnnData` always calls "obs" and "var". In contrast, `Daf` can store data for an arbitrary set of meaningfully named axes.
  * `Anndata` always contains a matrix property for these two axes called "X". Mercifully, the rest of the matrices are allowed to have meaningful names. In contrast, `Daf` allows storing an arbitrary set of meaningfully named matrices.
  * `AnnData` can only hold row-major matrices, while Julia defaults to column-major layout; `Daf` allows storing both layouts, sacrificing disk storage for performance.

Therefore, when viewing `Daf` data as `AnnData`, we pick two specific axes and rename them to "obs" and "var", pick a specific matrix property of these axes and rename it to "X", and [`relayout!`](@ref) it if needed so `AnnData` would be happy. We store the discarded names of the axes and matrix in unstructured annotations called `obs_is`, `var_is` and `X_is`. This allows us to reconstruct the original names when re-viewing the `AnnData` as `Daf` data.

The following `AnnData` can't be naively stored in `Daf`:

  * Non-scalars (e.g., mappings) inside `uns` unstructured annotations. The `Daf` equivalent is storing JSON string blobs, which is awkward to use. TODO: provide better API to deal with such data.
  * Data using nullable entries (e.g. a matrix with nullable integer entries). In contrast, `Daf` supports the convention that zero values are special. This only works in some cases (e.g., it isn't a good solution for Boolean data). It is possible of course to explicitly store Boolean masks and apply them to the data, but this is inconvenient. TODO: Have `Daf` natively support nullable/masked arrays.
  * Categorical data. Categorical vectors are therefore converted to simple strings. However, `Daf` doesn't support matrices of strings, so it doesn't support or convert categorical matrices.
  * Matrix data that only uses one of the axes (that is, `obsm` and `varm` data). The problem here is, paradoxically, that `Daf` supports such data "too well", by allowing multiple axes to be defined, and storing matrices based on any pair of axes. However, this requires the other axes to be explicitly created, and their information just doesn't exist in the `AnnData` data set. TODO: Allow unstructured annotations to store the entries of the other axis.

When viewing `AnnData` as `Daf`, we either ignore, warn, or treat as an error any such unsupported data.

!!! warning
    Square matrices accessed via `Daf` APIs will be the (column-major) **transpose** of the original `AnnData` (row-major) matrix.


Due to limitations of the `Daf` data model, square matrices are stored only in column-major layout. In contrast, `AnnData` square matrices (`obsp`, `varp`), are stored in row-major layout. We have several bad options to address this:

  * We can break the `Daf` invariant that all accessed data is column-major, at least for square matrices. This is bad because the invariant greatly simplifies `Daf` client code. Forcing clients to check the data layout and calling [`relayout!`](@ref) would add a lot of error-prone boilerplate to our users.
  * We can [`relayout!`](@ref) the data when copying it between `AnnData` and `Daf`. This is bad because it would force us to duplicate the data. More importantly, there is typically a good reason for the layout of the data. For example, assume a directed graph between cells. A common way to store is is to have a square matrix where each row contains the weights of the edges originating in one cell, connecting it to all other cells. This allows code to efficiently "loop on all cells; loop on all outgoing edges". If we [`relayout!`](@ref) the data, then such a loop would become extremely inefficient.
  * We can return the transposed matrix from `Daf`. This is bad because Julia code and Python code processing the "same" data would need to flip the indices (e.g., `outgoing_weight[from_cell, to_cell]` in Python vs. `outgoing_weight[to_cell, from_cell]` in Julia).

Having to pick between these bad options, we chose the last one as the lesser evil. The assumption is that Julia code is written separately from the Python code anyway. If the same algorithm is implemented in both systems, it would work (efficiently!) - that is, as long as the developer read this warning and flipped the order of the indices.

We do **not** have this problem with non-square matrices (e.g., the per-cell-per-gene `UMIs` matrix), since `Daf` allows for storing and accessing both layouts of the same data in this case. We simply populate `Daf` with the row-major data from `AnnData` and if asked for the outher layout, will [`relayout!`](@ref) it (and store/cache the result).
