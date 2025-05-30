```julia
encrypt_hill(plaintext::AbstractString, key::AbstractArray{Integer, 2})
```

Encrypts the given plaintext according to the Hill cipher. The key may be given as a matrix (that is, two-dimensional `Array{Int}`) or as a string.

If the key is given as a string, the string is converted to uppercase before use, and symbols are removed. It is assumed to be of square integer length, and the matrix entries are filled top-left to top-right, then next-top left to next-top right, and so on down to bottom-left to bottom-right. If the string is not of square integer length, an error is thrown.

The matrix must be invertible modulo 26. If it is not, an error is thrown.

---

### Examples

```julia
julia> encrypt_hill("Hello, World!", [1 2; 5 7]) # Encrypt the text "Hello, World!" with a Hill key of matrix `[1 2; 5 7]`
"PHHRGUWQRV"

julia> encrypt_hill("Hello, World!", "bcfh")
"PLHCGQWHRY"

julia> encrypt_hill("Hello", "bcfh") # If the plaintext-length is not a multiple of the dimension of the key matrix, it is padded with X
"PLHCIX"
```
