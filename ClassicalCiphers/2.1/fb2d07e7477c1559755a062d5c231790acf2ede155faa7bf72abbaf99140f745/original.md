```julia
decrypt_solitaire(string::AbstractString, initialDeck::AbstractVector{T}) where {T <: Integer}
```

Decrypts the given ciphertext according to the Solitaire cipher. The key may be given either as a vector initial deck, where the cards are 1 through 54 (the two jokers being 53, 54), or as a string. Schneier's keying algorithm is used to key the deck if the key is a string.

---

### Examples

```julia
julia> decrypt_solitaire("EXKYI ZSGEH UNTIQ", collect(1:54)) # as per https://www.schneier.com/code/sol-test.txt
"aaaaaaaaaaaaaaa"
```
