```
delrows(A::Union{Matrix, GDtype}; rows::Vector{<:Integer}=Int[], nodata=nothing, col=0)
```

Return a new matrix or GMTdataset where the rows listed in the vector of integers `rows` or rows found with other conditions were deleted.

### Args

  * `A`: Matrix or GMTdataset

### Kwargs

  * `rows`: Vector of integers specifying the rows to delete. Note: either this or the `nodata` option must be specified.
  * `nodata`: Value that indicates no data value. Rows where this value is found are deleted. Use $nodata=NaN$  to delete rows with NaN values. Note: either this or the `rows` option must be specified.
  * `col`: Column to check for `nodata`. the Default is to search in all columns. Use this option is  to restrict the search to a specific column.

### Examples

```julia
A = [1.0:6 10:10:60];
A[3] = NaN;
M1 = delrows(A, rows=[1,5])
M2 = delrows(M1, nodata=NaN)
M3 = delrows(M2, nodata=40, col=2)
```
