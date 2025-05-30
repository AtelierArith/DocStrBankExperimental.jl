```julia
encrypt_solitaire(string::AbstractString, initialDeck::AbstractVector{T}) where {T <: Integer}
```

Encrypts the given plaintext according to the Solitaire cipher. The key may be given either as a vector initial deck, where the cards are 1 through 54 (the two jokers being 53, 54), or as a string. Schneier's keying algorithm is used to key the deck if the key is a string.

---

### Examples

```julia
julia> encrypt_solitaire("Hello, World!", "crypto")
"GRNNQISRYA"
```
