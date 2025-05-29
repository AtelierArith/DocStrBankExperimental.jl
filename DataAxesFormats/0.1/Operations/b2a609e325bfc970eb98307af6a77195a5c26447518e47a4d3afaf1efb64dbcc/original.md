```
Significant(; high::StorageReal, low::Maybe{StorageReal} = nothing)
```

Element-wise operation that zeros all "insignificant" values. Significant values have a high absolute value. This is typically used to prune matrices of effect sizes (log of ratio between a baseline and some result) for heatmap display. For example, log base 2 of gene expression ratio is typically considered significant if it is at least 3 (that is, a ratio at least 8x or at most 1/8x); for genes that have a significant effect, we typically display all entries with a log of at least 2 (that is, a ratio of at least 4x or at most 1/4x).

For scalars, this operation makes no sense so fails with an error.

**Parameters**:

`high` - A value is considered significant if its absolute value is higher than this. If all values in a vector (or a matrix column) are less than this, then all the vector (or matrix column) entries are zeroed. There's no default.

`low` - If there is at least one significant value in a vector (or a matrix column), then zero all entries that are lower than this. By default, this is the same as the `high` value. Setting it to a lower value will preserve more entries, but only for vectors (or matrix columns) which contain at least some significant data.
