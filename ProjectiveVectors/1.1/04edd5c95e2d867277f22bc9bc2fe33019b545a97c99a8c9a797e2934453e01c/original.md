```
norm(z::PVector{T,N}, p::Real=2)::NTuple{N, real(T)}
```

Compute the `p`-norm of `z` per vector space. This always returns a `Tuple`.

## Example

```julia-repl
julia> norm(embed([1, 2, 3, 4, 5], (2, 3)))
(2.449489742783178, 7.14142842854285)

julia> norm(embed([1, 2, 3, 4, 5]))
(7.483314773547883,)
```
