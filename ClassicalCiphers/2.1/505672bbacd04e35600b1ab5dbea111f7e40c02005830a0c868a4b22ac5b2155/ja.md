```julia
encrypt_railfence(input::AbstractString, n_rails::Integer)
```

See [`https://en.wikipedia.org/wiki/Rail_fence_cipher`](https://en.wikipedia.org/wiki/Rail_fence_cipher).

---

### 例

```julia
julia> encrypt_railfence("WE ARE DISCOVERED. FLEE AT ONCE", 3) # これは上の行列を行ごとに読み取ります
"WECRFACERDSOEE.LETNEAIVDEO"
```
