Arguably the most simple of the classical ciphers, the substitution cipher works by creating an arbitrary substitution dictionary; e.g.,

```julia
'a' => 'x'
'b' => 'g'
'c' => 'l'
...
```

This dictionary then replaces every corresponding letter in the plaintext input with a different letter (as specified by the dictionary input.)

The function `encrypt_substitution` will either take this dictionary as its second parameter, *or* it can construct the dictionary itself:

```julia
encrypt_substitution(plaintext, Dict(...))
encrypt_substitution(plaintext, "abcdefghijklmnopqrstuvwxyz", "zyxwvutsrqponmlkjihgfedcba") # this will create the dictionary 'a' => 'z', 'b' => 'y', ..., 'z' => 'a'
encrypt_substitution(plaintext, "zyxwvutsrqponmlkjihgfedcba") # this will create the dictionary 'a' => 'z', 'b' => 'y', ..., 'z' => 'a' by assuming the keys in the substitution dictionary
```

*All characters undefined in the dictionary are preserved by default; this includes punctionation, spaces, and cases.*  This means that, when using a dictionary, strings are not automatically converted into uppercase.

As per convention, the output will always be uppercase.

For more information, see [`https://en.wikipedia.org/wiki/Substitution_cipher`](https://en.wikipedia.org/wiki/Substitution_cipher).

---

### Examples

```julia
julia> encrypt_monoalphabetic("Hello, World!", "DEFGHIJKLMNOPQRSTUVWXYZABC")
"KHOOR, ZRUOG!"

julia> encrypt_monoalphabetic("aBcbDd", Dict{Char, Char}('a' => '5', 'B' => '@', 'b' => 'o'))
"5@coDd"

julia> encrypt_monoalphabetic("Hello, this is plaintext", "abcdefghijklmnopqrstuvwxyz", "qwertyuiopasdfghjklzxcvbnm")
"ITSSG, ZIOL OL HSQOFZTBZ"

julia> encrypt_monoalphabetic("Hello, this is plaintext", "qwertyuiopasdfghjklzxcvbnm")
"ITSSG, ZIOL OL HSQOFZTBZ"

julia> encrypt_monoalphabetic("xyz", Dict('x' => 'd', 'y' => 'e', 'z' => 't'))
"det"
```
