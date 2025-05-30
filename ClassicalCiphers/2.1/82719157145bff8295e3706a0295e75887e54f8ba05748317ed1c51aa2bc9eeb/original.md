```julia
decrypt_caesar(ciphertext, key::Integer)
decrypt_caesar(ciphertext)
```

Decrypts the given ciphertext according to the Caesar cipher. The key is given as an integer, being the offset of each character; so `decrypt_caesar("abcd", 1) == "zabc"`.

Converts the input to lowercase, but retains symbols.

Traditionally, the Caesar cipher was used with a shift of 3, so this is the method it will fall back to if only given plaintext.

---

### Examples

```julia
julia> decrypt_caesar("Khoor, Zruog!", 3)
"hello, world!"
```
