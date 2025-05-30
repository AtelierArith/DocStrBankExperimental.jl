```julia
decrypt_playfair(ciphertext, key::Array{Char, 2}; combined::AbstractPair{Char, Char} = ('I', 'J'))
```

Decrypts the given ciphertext according to the Playfair cipher.

Does not attempt to delete X's inserted as padding for double letters.

---

### Examples

```julia
julia> decrypt_playfair("RMRMFWYE", "playfair example")
"ixixyzax"
```
