```julia
encrypt_affine(plaintext, mult::Integer, add::Integer; offset::Integer = 0)
```

Encrypts the given plaintext according to the Affine cipher. The key is given as a pair of integers: first the multiplier, then the additive constant.

The multiplier must be coprime to 26. If it is not, an error is thrown.

Converts the input to uppercase, but retains symbols.

Optional argument: `offset=0`, which specifies what number 'a' should be considered as.

---

### Examples

```julia
julia> encrypt_affine("Hello, World!", 3, 4)
"ZQLLU, SUDLN!"
```
