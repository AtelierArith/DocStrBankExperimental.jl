```julia
decrypt_atbash(ciphertext, alphabet)
```

A special case of the substitution cipher, the Atbash cipher substitutes a given alphabet with its reverse:

```julia
decrypt_atbash(ciphertext, "abcdefghijklmnopqrstuvwxyz") == decrypt_substitution(ciphertext, "zyxwvutsrqponmlkjihgfedcba", "abcdefghijklmnopqrstuvwxyz")
decrypt_atbash(ciphertext, "abcdefghijklmnopqrstuvwxyz") == decrypt_substitution(ciphertext, "zyxwvutsrqponmlkjihgfedcba"; reverse_dict = true)
```

*Omitting the alphabet, it will assume you are using the English alphabet.*

---

### Examples

```julia
julia> encrypt_atbash("some text", "abcdefghijklmnopqrstuvwxyz")
"HLNV GVCG"

julia> decrypt_atbash("HLNV GVCG", "abcdefghijklmnopqrstuvwxyz")
"some text"
```
