Create a feature matrix for a list of vectors. In the resulting matrix, each column c represents the alignment of one vector with the SCS for the parameter vectors, each row r represents one feature, and each cell value r,c is the value for feature r in vector c.

# Examples

```jldoctest
julia> featurematrix([1,3,5], [4,5,6])
5×2 Matrix{Any}:
	1          nothing
	3          nothing
	nothing  4
	5         5
	nothing  6	
```

```julia
featurematrix(v; norm, cf)

```
