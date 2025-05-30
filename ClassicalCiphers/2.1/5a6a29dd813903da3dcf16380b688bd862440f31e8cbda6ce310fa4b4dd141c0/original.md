```julia
decrypt_vigenere(ciphertext, key::Array)
decrypt_vigenere(plaintext, key::AbstractString)
```

Decrypts the given string using the Vigenere cipher according to the given vector of offsets. For example, `decrypt_vigenere("ac", [0, 1])` returns `"ab"`.

---

### Examples

```julia
julia> decrypt_vigenere("HFLMOXOSLE", [0, 1]) # Notice that the offset `0` corresponds to the key `a`.
"helloworld"
```
