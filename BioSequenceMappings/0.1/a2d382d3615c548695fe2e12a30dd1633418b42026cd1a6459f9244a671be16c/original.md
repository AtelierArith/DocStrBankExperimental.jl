```
Alignment(data::AbstractMatrix, alphabet; kwargs...)
```

`data` is a matrix of integers, with sequences stored in columns. `alphabet` can be either

  * an `Alphabet`
  * `nothing`: no conversion from integers to biological symbols.
  * something to build an alphabet from (*e.g.* a symbol like `:aa`, a string, ...).   The constructor `Alphabet` will be called like so: `Alphabet(alphabet)`.

If the types of `alphabet` and `data` mismatch, `data` is converted.

`data` can also have the following shape:

  * vector of integer vectors, *e.g.* [[1,2], [3,4]]: each element is considered as a sequence
  * vector of integers: single sequence alignment
