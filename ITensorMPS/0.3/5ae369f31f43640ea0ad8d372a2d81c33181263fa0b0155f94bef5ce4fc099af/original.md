```
outer(x::MPS, y::MPS; <keyword argument>) -> MPO
```

Compute the outer product of `MPS` `x` and `MPS` `y`, returning an `MPO` approximation. Note that `y` will be conjugated.

In Dirac notation, this is the operation `|x⟩⟨y|`.

If you want an outer product of an MPS with itself, you should call `outer(x', x; kwargs...)` so that the resulting MPO has site indices with indices coming in pairs of prime levels of 1 and 0. If not, the site indices won't be unique which would not be an outer product.

For example:

```julia
s = siteinds("S=1/2", 5)
x = random_mps(s)
y = random_mps(s)
outer(x, y) # Incorrect! Site indices must be unique.
outer(x', y) # Results in an MPO with pairs of primed and unprimed indices.
```

This allows for more general outer products, such as more general MPO outputs which don't have pairs of primed and unprimed indices, or outer products where the input MPS are vectorizations of MPOs.

For example:

```julia
s = siteinds("S=1/2", 5)
X = MPO(s, "Id")
Y = MPO(s, "Id")
x = convert(MPS, X)
y = convert(MPS, Y)
outer(x, y) # Incorrect! Site indices must be unique.
outer(x', y) # Incorrect! Site indices must be unique.
outer(addtags(x, "Out"), addtags(y, "In")) # This performs a proper outer product.
```

The keyword arguments determine the truncation, and accept the same arguments as `contract(::MPO, ::MPO; kwargs...)`.

See also [`apply`](@ref), [`contract`](@ref).
