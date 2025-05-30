```julia
encrypt_vigenere(plaintext, key::Array)
encrypt_vigenere(ciphertext, key::AbstractString)
```

Encrypts the given string using the Vigenere cipher according to the given vector of offsets. For example, `encrypt_vigenere("ab", [0, 1])` returns `"AC"`.

---

### Examples

```julia
julia> encrypt_vigenere("Hello, World!", "ab")
"HFLMOXOSLE"
```
