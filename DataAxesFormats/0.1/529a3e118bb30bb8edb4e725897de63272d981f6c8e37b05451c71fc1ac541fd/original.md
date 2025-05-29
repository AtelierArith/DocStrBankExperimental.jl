The `DataAxesFormats` package provides a uniform generic interface for accessing 1D and 2D data arranged along some set of axes. This is a much-needed generalization of the [AnnData](https://pypi.org/project/anndata/) functionality. The key features are:

  * The data model [`StorageTypes`](@ref) include (1) some axes with named entries, (2) vector data indexed by a single axis, (3) matrix data indexed by a pair of axes, and also (4) scalar data (anything not tied to some axis).
  * Explicit control over 2D data [`MatrixLayouts`](@ref) (row or column major), with support for both dense and sparse matrices, both of which are crucial for performance.
  * Out of the box, allow storing the data in memory (using [`MemoryDaf`](@ref)), directly inside [HDF5](https://www.hdfgroup.org/solutions/hdf5/) files (using [`H5df`](@ref)), or as a collection of simple files in a directory (using [`FilesDaf`](@ref)), which works nicely with tools like `make` for automating computation pipelines.
  * Import and export to/from [`AnnDataFormat`](@ref) for interoperability with non-`Daf` tools.
  * Implementation with a focus on memory-mapping to allow for efficient processing of large data sets (in theory, larger than the system's memory). In particular, merely opening a data set is a fast operation (almost) regardless of its size.
  * Well-defined interfaces for implementing additional storage [`Formats`](@ref).
  * Creating [`Chains`](@ref) of data sets, allowing zero-copy reuse of common data between multiple computation pipelines.
  * [`Concat`](@ref) multiple data sets into a single data set along one or more axes.
  * A [`Query`](@ref) language for accessing the data, providing features such as slicing, aggregation and filtering, and making [`Views`](@ref) and [`Copies`](@ref) based on these queries.
  * Self documenting [`Computations`](@ref) with an explicit [`Contracts`](@ref) describing and enforcing the inputs and outputs, and [`Adapters`](@ref) for applying the computation to data of a different format.

!!! note
    The top-level `DataAxesFormats` module re-exports all(most) everything from the sub-modules, so you can directly access any exported symbol by `using DataAxesFormats` (or `import DataAxesFormats: MemoryDaf`), instead of having to import or use qualified names (such as `DataAxesFormats.MemoryFormat.MemoryDaf`).


The `Daf` data sets type hierarchy looks like this:

```
DafReader (abstract type)
├─ DafReadOnly (abstract type)
│  ├─ DafReadOnlyWrapper (created by read_only)
│  ├─ DafView (created by viewer)
│  └─ DafChainReader (created by chain_reader)
└─ DafWriter (abstract type)
   ├─ DafChainWriter (created by chain_writer)
   ├─ MemoryDaf
   ├─ FilesDaf
   └─ H5df
```
