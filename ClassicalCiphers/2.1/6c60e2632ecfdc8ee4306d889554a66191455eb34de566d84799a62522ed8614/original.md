```julia
encrypt_caesar(plaintext, key::Integer)
encrypt_caesar(plaintext)
```

Encrypts the given plaintext according to the Caesar cipher. The key is given as an integer, being the offset of each character; so `encrypt_caesar("abc", 1) == "BCD"`.

Converts the input to uppercase, but retains symbols.

Traditionally, the Caesar cipher was used with a shift of 3, so this is the method it will fall back to if only given plaintext.

---

### Examples

```julia
julia> encrypt_caesar("Hello, World!", 3)
"KHOOR, ZRUOG!"
```
