Arguably the most simple of the classical ciphers, the substitution cipher works by creating an arbitrary substitution dictionary; e.g.,

```julia
'a' => 'x'
'b' => 'g'
'c' => 'l'
...
```

This dictionary then replaces every corresponding letter in the plaintext input with a different letter (as specified by the dictionary input.)

The function `decrypt_substitution` will either take this dictionary as its second parameter, *or* it can construct the dictionary itself:

```julia
decrypt_substitution(ciphertext, Dict(...); reverse_dict = true)
decrypt_substitution(ciphertext, "abcdefghijklmnopqrstuvwxyz", "zyxwvutsrqponmlkjihgfedcba"; reverse_dict = true) # this will create the dictionary 'a' => 'z', 'b' => 'y', ..., 'z' => 'a'
decrypt_substitution(ciphertext, "zyxwvutsrqponmlkjihgfedcba"; reverse_dict = true) # this will create the dictionary 'a' => 'z', 'b' => 'y', ..., 'z' => 'a' by assuming the keys in the substitution dictionary
```

*All characters undefined in the dictionary are preserved by default; this includes punctionation, spaces, and cases.*  This means that, when using a dictionary, strings are not automatically converted into lowercase.

*If `reverse_dict` is set to true (as it is by default), the input dictionary is assumed to be the same used to *en*crypt, meaning it is reversed in order to *decrypt* the ciphertext.*

As per convention, the output will always be lowercase.

For more information, see [`https://en.wikipedia.org/wiki/Substitution_cipher`](https://en.wikipedia.org/wiki/Substitution_cipher).

---

### Examples

```julia
julia> decrypt_monoalphabetic("ITSSG, ZIOL OL HSQOFZTBZ", "abcdefghijklmnopqrstuvwxyz", "qwertyuiopasdfghjklzxcvbnm", reverse_dict = true)
"hello, this is plaintext"

julia> decrypt_monoalphabetic("Khoor, Zruog!", "DEFGHIJKLMNOPQRSTUVWXYZABC")
"hello, world!"
```
