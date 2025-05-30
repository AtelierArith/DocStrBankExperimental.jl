```julia
encrypt_railfence(input::AbstractString, n_rails::Integer)
```

See [`https://en.wikipedia.org/wiki/Rail_fence_cipher`](https://en.wikipedia.org/wiki/Rail_fence_cipher).

---

### Examples

```julia
julia> decrypt_railfence("WECRFACERDSOEE.LETNEAIVDEO", 3)
"wearediscovered.fleeatonce"
```
