```julia
decrypt_hill(ciphertext, key::AbstractArray{T, 2}) where {T <: Integer}
```

---

### Examples

```julia
julia> decrypt_hill("PLHCGQWHRY", [1 2; 5 7]) # Decrypt the text "PLHCGQWHRY" with key of `[1 2; 5 7]`
"helloworld"

julia> decrypt_hill("PLHCGQWHRY", "bcfh")
"helloworld"

julia> decrypt_hill("PLHCIX", "bcfh") # If the plaintext-length is not a multiple of the dimension of the key matrix, it is padded with X
"hellox"
```
