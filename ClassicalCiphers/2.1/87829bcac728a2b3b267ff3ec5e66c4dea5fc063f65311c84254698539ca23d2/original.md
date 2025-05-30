```julia
crack_vigenere(plaintext; keylength::Integer = 0)
```

Cracks the given text encrypted with the Vigenere cipher.

Returns `(derived key, decrypted plaintext)`.

Optional parameters: `keylength=0`: if the key length is known, specifying it may help the solver. If 0, the solver will attempt to derive the key length using the index of coincidence.

---

### Examples

```julia
julia> crack_vigenere(str)
```
