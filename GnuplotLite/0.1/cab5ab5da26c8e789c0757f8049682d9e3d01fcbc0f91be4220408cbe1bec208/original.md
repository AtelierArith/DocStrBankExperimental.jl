```
 send(::Pair{String,Matrix{T}}) where T <: Number
```

Send a matrix to Gnuplot, storing it in a variable. This variant assumes the matrix gets integer indices from `[0..N-1]`, as described in the Gnuplot documentation for uniform matrices.

Returns a [`Msg`](@ref).
