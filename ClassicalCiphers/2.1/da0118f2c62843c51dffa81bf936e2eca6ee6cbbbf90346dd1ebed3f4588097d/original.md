```julia
decrypt_affine(ciphertext, mult::Integer, add::Integer; offset::Integer=0)
```

Decrypts the given ciphertext according to the Affine cipher. The key is given as a pair of integers: first the multiplier, then the additive constant.

The multiplier must be coprime to 26. If it is not, an error is thrown.

Converts the input to lowercase, but retains symbols.

Optional argument: `offset=0`, which specifies what number 'a' should be considered as.

---

### Examples

```julia
julia> decrypt_affine("ZQLLU, SUDLN!", 3, 4)
"hello, world!"
```
