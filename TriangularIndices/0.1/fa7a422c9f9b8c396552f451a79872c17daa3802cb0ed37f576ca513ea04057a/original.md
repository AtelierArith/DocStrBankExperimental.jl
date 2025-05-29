`UpperTriangularIndices` - Indices of a triangular matrix.

`UpperTriangleIndices(n)` yields iterator of all the (row, column) indices of an upper triangular matrix of side-length `n`. (For an upper triangular matrix, `n` only determines the length of the sequence. It is not used in computing indices.)

`UpperTriangleIndices(A)` where `A` is a square matrix yields an iterator fitting the size of `A`.

Indexing operations involve square roots, so are slightly slower than iteration.

Note: The implementation may change in future releases. Code that uses the fields of this struct directly is likely to break.
