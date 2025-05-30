```julia
encrypt_railfence(input::AbstractString, n_rails::Integer)
```

See [`https://en.wikipedia.org/wiki/Rail_fence_cipher`](https://en.wikipedia.org/wiki/Rail_fence_cipher).

---

### Examples

```julia
julia> encrypt_railfence("WE ARE DISCOVERED. FLEE AT ONCE", 3) # this reads the above matrix row by row
"WECRFACERDSOEE.LETNEAIVDEO"
```
