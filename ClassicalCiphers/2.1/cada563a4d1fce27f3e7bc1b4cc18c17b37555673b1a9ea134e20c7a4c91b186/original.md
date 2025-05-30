```julia
decrypt_portas(ciphertext, key::AbstractString)
```

Decrypts the given ciphertext with the Portas cipher.

The key must be given as a string, whose characters are letters.

Converts the text to lowercase.

---

### Examples

```julia
julia> decrypt_portas("URYYB, JBEYQ!", "ab")
"hello, world!"
```
