```julia
encrypt_portas(plaintext, key_in::AbstractString)
```

Encrypts the given plaintext with the Portas cipher.

The key must be given as a string, whose characters are letters.

Converts the text to uppercase.

---

### Examples

```julia
julia> encrypt_portas("Hello, World!", "ab")
"URYYB, JBEYQ!"
```
