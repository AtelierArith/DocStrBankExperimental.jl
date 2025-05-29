indextype(A)

gives the expected index type for an array, or array-like object. For example, if it is vector-like it will return `Tuple{Int}`, or if it is matrix-like it will return `Tuple{Int,Int}`. Other types may have non-integer based indexing.
