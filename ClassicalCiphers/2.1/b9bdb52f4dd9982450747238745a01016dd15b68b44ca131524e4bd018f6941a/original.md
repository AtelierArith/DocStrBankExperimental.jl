```julia
encrypt_playfair(plaintext, key::Array{Char, 2}; stripped::Bool = false, combined::AbstractPair{Char, Char} = ('I', 'J'))
```

Encrypts the given plaintext according to the Playfair cipher. Throws an error if the second entry in the `combined` tuple is present in the key.

Optional parameters:

`stripped=false`. When set to true, `encrypt_playfair` skips   converting the plaintext to uppercase, removing punctuation, and   combining characters which are to be combined in the key. `combined=('I', 'J')`, marks the characters which are to be combined in the text.   Only the first of these two may be present in the output of `encrypt_playfair`.

---

### Examples

```julia
julia> encrypt_playfair("Hello, World!", "playfair example")
"DMYRANVQCRGE"

julia> arr = ['P' 'L' 'A' 'Y' 'F'; 'I' 'R' 'E' 'X' 'M'; 'B' 'C' 'D' 'G' 'H'; 'K' 'N' 'O' 'Q' 'S'; 'T' 'U' 'V' 'W' 'Z'];

julia> encrypt_playfair("Hello, World!", arr) # Encrypt the same text using an explicitly specified keysquare
"DMYRANVQCRGE"

julia> encrypt_playfair("IJXYZA", "PLAYFIREXM", combined=('I', 'J')) # Optionally specify the two letters which are to be combined (default 'I','J')
"RMRMFWYE"

julia> encrypt_playfair("IJXYZA", "PLAYFIREXM", combined=('X', 'Z'))
"BSGXEY"
```
