```
Xs = source(X=nothing)
```

Define, a learning network `Source` object, wrapping some input data `X`, which can be `nothing` for purposes of exporting the network as stand-alone model. For training and testing the unexported network, appropriate vectors, tables, or other data containers are expected.

The calling behaviour of a `Source` object is this:

```julia
Xs() = X
Xs(rows=r) = selectrows(X, r)  # eg, X[r,:] for a DataFrame
Xs(Xnew) = Xnew
```

See also: [`MLJBase.prefit`](@ref), [`sources`](@ref), [`origins`](@ref), [`node`](@ref).
