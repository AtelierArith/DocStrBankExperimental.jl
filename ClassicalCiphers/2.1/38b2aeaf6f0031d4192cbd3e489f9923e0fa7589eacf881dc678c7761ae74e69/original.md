```julia
crack_caesar(ciphertext; cleverness::Integer = 1)
```

Cracks the given ciphertext according to the Caesar cipher. Returns `(plaintext, key::Integer)`, such that `encrypt_caesar(plaintext, key)` would return ciphertext.

With `cleverness=0`, simply does the shift that maximises e's frequency. With `cleverness=1`, maximises the string's total fitness.

Converts the input to lowercase.

---

### Examples

```julia
julia> crack_caesar("Khoor, Zruog!")
("hello, world!", 3)
```
