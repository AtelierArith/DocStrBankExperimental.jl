```
ARFFReader
```

An object holding an IO stream of an ARFF file, used to access its data.

Header information is in the `header` field, of type [`ARFFHeader`](@ref).

It has the following functionality:

  * `nextrow(r)` returns the next row of data as a `NamedTuple{names, types}`, or `nothing` if everything has been read.
  * `read(r, [n])` reads up to `n` rows as a vector.
  * `read!(xs, r)` reads up to `length(xs)` rows into the given vector, returning the number of rows read.
  * `close(r)` closes the underlying IO stream, unless it was created with `own=false`.
  * `eof(r)` tests whether the IO stream is at the end.
  * Iteration yields rows of `r`.
  * It satisfies the `Tables.jl` interface, so e.g. `DataFrame(r)` does what you think.
