A `Daf` storage format in an HDF5 disk file. This is the "native" way to store `Daf` data in HDF5 files, which can be used to contain "anything", as HDF5 is essentially "a filesystem inside a file", with "groups" instead of directories and "datasets" instead of files. Therefore HDF5 is very generic, and there are various specific formats which use specific internal structure to hold some data in it - for example, `h5ad` files have a specific internal structure for representing [AnnData](https://pypi.org/project/anndata/) objects. To represent `Daf` data in HDF5 storage, we use the following internal structure (which

is **not** compatible with `h5ad`):

  * The HDF5 file may contain `Daf` data directly in the root group, in which case, it is restricted to holding just a single `Daf` data set. When using such a file, you automatically access the single `Daf` data set contained in it. By convention such files are given a `.h5df` suffix.
  * Alternatively, the HDF5 file may contain `Daf` data inside some arbitrary group, in which case, there's no restriction on the content of other groups in the file. Such groups may contain other `Daf` data (allowing for multiple `Daf` data sets in a single file), and/or non-`Daf` data. When using such a file, you need to specify the name of the group that contains the `Daf` data set you are interested it. By convention, at least if such files contain "mostly" (or only) `Daf` data sets, they are given a `.h5dfs` suffix, and are accompanied by some documentation describing the top-level groups in the file.
  * Under the `Daf` data group, there are 4 sub-groups: `scalars`, `axes`, `vectors` and `matrices` and a `daf` dataset.
  * To future-proof the format, the `daf` dataset will contain a vector of two integers, the first acting as the major version number and the second as the minor version number, using [semantic versioning](https://semver.org/). This makes it easy to test whether some group in an HDF5 file does/n't contain `Daf` data, and which version of the internal structure it is using. Currently the only defined version is `[1,0]`.
  * The `scalars` group contains scalar properties, each as its own "dataset". The only supported scalar data types are these included in [`StorageScalar`](@ref). If you **really** need something else, serialize it to JSON and store the result as a string scalar. This should be **extremely** rare.
  * The `axes` group contains a "dataset" per axis, which contains a vector of strings (the names of the axis entries).
  * The `vectors` group contains a sub-group for each axis. Each such sub-group contains vector properties. If the vector is dense, it is stored directly as a "dataset". Otherwise, it is stored as a group containing two vector "datasets": `nzind` is containing the indices of the non-zero values, and `nzval` containing the actual values. See Julia's `SparseVector` implementation for details. The only supported vector element types are these included in [`StorageScalar`](@ref), same as [`StorageVector`](@ref).
  * The `matrices` group contains a sub-group for each rows axis, which contains a sub-group for each columns axis. Each such sub-sub group contains matrix properties. If the matrix is dense, it is stored directly as a "dataset" (in column-major layout). Otherwise, it is stored as a group containing three vector "datasets": `colptr` containing the indices of the rows of each column in `rowval`, `rowval` containing the indices of the non-zero rows of the columns, and `nzval` containing the non-zero matrix entry values. See Julia's `SparseMatrixCSC` implementation for details. The only supported matrix element types are these included in [`StorageReal`](@ref) - this explicitly excludes matrices of strings, same as [`StorageMatrix`](@ref).
  * All vectors and matrices are stored in a contiguous way in the file, which allows us to efficiently memory-map them.

That's all there is to it. Due to the above restrictions on types and layout, the metadata provided by HDF5 for each "dataset" is sufficient to fully describe the data, and one should be able to directly access it using any HDF5 API in any programming language, if needed. Typically, however, it is easiest to simply use the Julia `Daf` package to access the data.

Example HDF5 structure:

```
example-daf-dataset-root-group/
├─ daf
├─ scalars/
│  └─ version
├─ axes/
│  ├─ cell
│  └─ gene
├─ vectors/
│  ├─ cell/
│  │  └─ batch
│  └─ gene/
│     └─ is_marker
└─ matrices/
   ├─ cell/
   │   ├─ cell/
   │   └─ gene/
   │      └─ UMIs/
   │         ├─ colptr
   │         ├─ rowval
   │         └─ nzval
   └─ gene/
      ├─ cell/
      └─ gene/
```

!!! note
    When creating an HDF5 file to contain `Daf` data, you should specify `;fapl=HDF5.FileAccessProperties(;alignment=(1,8))`. This ensures all the memory buffers are properly aligned for efficient access. Otherwise, memory mapping will be **much** less efficient. A warning is therefore generated whenever you try to access `Daf` data stored in an HDF5 file which does not enforce proper alignment.


!!! note
    Deleting data from an HDF5 file does not reuse the abandoned storage. In general if you want to reclaim that storage, you will need to repack the file, which will invalidate any memory-mapped buffers created for it. Therefore, if you delete data (e.g. using [`delete_vector!`](@ref)), you should eventually abandon the `H5df` object, repack the HDF5 file, then create a new `H5df` object to access the repacked data.


!!! note
    The code here assumes the HDF5 data obeys all the above conventions and restrictions (that said, code will be able to access vectors and matrices stored in unaligned, chunked and/or compressed formats, but this will be much less efficient). As long as you only create and access `Daf` data in HDF5 files using [`H5df`](@ref), then the code will work as expected (assuming no bugs). However, if you do this in some other way (e.g., directly using some HDF5 API in some arbitrary programming language), and the result is invalid, then the code here may fails with "less than friendly" error messages.

