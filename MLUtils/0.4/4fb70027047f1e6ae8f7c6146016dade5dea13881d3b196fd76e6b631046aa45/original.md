```
splitobs([rng,] data; at, shuffle=false, stratified=nothing) -> Tuple
```

Partition the `data` into two or more subsets.

The argument `at` specifies how to split the data:

  * When `at` is a number between 0 and 1, this specifies the proportion in the first subset.
  * When `at` is an integer, it specifies the number of observations in the first subset.
  * When `at` is a tuple, entries specifies the number or proportion in each subset, except

for the last which will contain the remaning observations.  The number of returned subsets is `length(at)+1`.

If `shuffle=true`, randomly permute the observations before splitting. A random number generator `rng` can be optionally passed as the first argument.

If `stratified` is not `nothing`, it should be an array of labels with the same length as the data. The observations will be split in such a way that the proportion of each label is preserved in each subset.

Supports any datatype implementing [`numobs`](@ref). 

It relies on [`obsview`](@ref) to create views of the data.

# Examples

```jldoctest
julia> splitobs(reshape(1:100, 1, :); at=0.7)  # simple 70%-30% split, of a matrix
([1 2 … 69 70], [71 72 … 99 100])

julia> data = (x=ones(2,10), n=1:10)  # a NamedTuple, consistent last dimension
(x = [1.0 1.0 … 1.0 1.0; 1.0 1.0 … 1.0 1.0], n = 1:10)

julia> splitobs(data, at=(0.5, 0.3))  # a 50%-30%-20% split, e.g. train/test/validation
((x = [1.0 1.0 … 1.0 1.0; 1.0 1.0 … 1.0 1.0], n = 1:5), (x = [1.0 1.0 1.0; 1.0 1.0 1.0], n = 6:8), (x = [1.0 1.0; 1.0 1.0], n = 9:10))

julia> train, test = splitobs((reshape(1.0:100.0, 1, :), 101:200), at=0.7, shuffle=true);  # split a Tuple

julia> vec(test[1]) .+ 100 == test[2]
true

julia> splitobs(1:10, at=0.5, stratified=[0,0,0,0,1,1,1,1,1,1]) # 2 zeros and 3 ones in each subset
([1, 2, 5, 6, 7], [3, 4, 8, 9, 10])
```
