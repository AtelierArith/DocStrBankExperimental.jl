```
PyArrowTable(py)
```

Wraps the python object `py` which corresponds to a pyarrow table to provide a Tables.jl-compatible interface.

Supports:

  * Property access to access the properties of the underlying pyarrow table (plus `table.py` to access the raw pyarrow table object). These yields PythonCall `Py` objects, which may need to be converted with `pyconvert`.
  * Indexing to access columns (`table[0]`, `table["col_name"]`). This also yields raw `Py` objects (which are not even `<: AbstractVector`).
  * the Tables.jl columnar interface, so e.g. `DataFrame(table)` should work. The columns are `PyArray`'s (i.e. `AbstractVector`'s pointing to python objects), or `ChainedVector`'s with `PyArray` subcomponents (if there is more than 1 batch).
  * DataAPI's `ncol` and `nrow` accessors.
  * datetime objects convertible to `np.datetime64`. `PyArrowTable` will convert to `np.datetime64`, which will convert the timezone to UTC using the timezone specified in the original object, or using the local timezone if one is not present (see: https://stackoverflow.com/a/25163415/20471121).

Does not yet support:

  * DataAPI's metadata-related functions
  * `Tables.partitions` to iterate record batches

This functionality may be added in future non-breaking releases.

## Example

```julia
using DataFrames, PyArrow
feather = pyimport("pyarrow.feather")
table = feather.read_table("table.arrow") # example
df = DataFrame(PyArrowTable(table)) # now we have a DataFrame with Py types

df_jl = mapcols(v -> pyconvert.(Any, v), df) # now we have Julia types
```
