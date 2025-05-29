Finite set whose elements are rows of a table.

The underlying table should be compliant with Tables.jl. For the sake of uniformity, the rows are provided as named tuples, which assumes that the table is not "extremely wide". This should not be a major limitation in practice but see the Tables.jl documentation for further discussion.
