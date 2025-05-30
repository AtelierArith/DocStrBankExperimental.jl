```julia
crack_affine(ciphertext; mult::Integer = 0, add::Integer = -1)
```

Cracks the given ciphertext according to the Affine cipher. Returns `((multiplier, additive constant), decrypted string)`.

Converts the input to lowercase, but retains symbols.

Optional arguments: `mult=0`, which specifies the multiplier if known; `add=-1`, which specifies the additive constant if known.

---

### Examples

```julia
julia> crack_affine("ZQLLU, SUDLN!")
("hello, world!", (3, 4))
```
