```julia
encrypt_atbash(plaintext, alphabet)
```

A special case of the substitution cipher, the Atbash cipher substitutes a given alphabet with its reverse:

```julia
encrypt_atbash(plaintext, "abcdefghijklmnopqrstuvwxyz") == encrypt_substitution(plaintext, "abcdefghijklmnopqrstuvwxyz", "zyxwvutsrqponmlkjihgfedcba")
```

*Omitting the alphabet, it will assume you are using the English alphabet.*
