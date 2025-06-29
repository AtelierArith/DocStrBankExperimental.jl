Implementation of the notation `..` for indexing arrays. It's similar to the Python `...` in that it means 'all the columns before (or after)'.

`..` slurps dimensions greedily, meaning that the first occurrence of `..` in an index expression creates as many slices as possible. Other instances of `..` afterward are treated simply as slices. Usually, you should only use one instance of `..` in an indexing expression to avoid possible confusion.

# Example

```jldoctest
julia> A = Array{Int}(undef, 2, 4, 2);

julia> A[.., 1] = [2 1 4 5
           2 2 3 6];

julia> A[.., 2] = [3 2 6 5
           3 2 6 6];

julia> A[:, :, 1] == [2 1 4 5
           2 2 3 6]
true

julia> A[1, ..] = reshape([3 4
               5 6
               4 5
               6 7], 1, 4, 2) # drops singleton dimension
...

julia> B = [3 4
           5 6
           4 5
           6 7];

julia> B == reshape(A[1, ..], 4, 2)
true
```
