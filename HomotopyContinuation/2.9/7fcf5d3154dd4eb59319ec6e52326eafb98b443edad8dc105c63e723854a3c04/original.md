```
witness_set(F; codim = nvariables(F) - length(F), dim = nothing, options...)
```

Compute a [`WitnessSet`](@ref) for `F` in the given dimension (resp. codimension) by sampling a random (affine) linear subspace. After constructing the system this calls [`solve`](@ref) with the provided `options`.

```
witness_set(F, L; options...)
```

Compute [`WitnessSet`](@ref) for `F` and the (affine) linear subspace `L`.

```
witness_set(W::WitnessSet, L; options...)
```

Compute a new [`WitnessSet`](@ref) with the (affine) linear subspace `L` by moving the linear subspace stored in `W` to `L`.

### Example

```julia-repl
julia> @var x y;
julia> F = System([x^2 + y^2 - 5], [x, y])
System of length 1
 2 variables: x, y

 -5 + x^2 + y^2

julia> W = witness_set(F)
Witness set for dimension 1 of degree 2
```
