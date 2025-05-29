Accent word according to specified system of accent placement.

```julia
accentword(wrd, placement)
accentword(wrd, placement, ortho)

```

# Parameters

  * `wrd` is a string value representing a single lexical token.
  * `placement` is one of `:RECESSIVE` for recessive accent

or `:PENULT` for persistent accent on the penultimate syllable.

Note that it is not possible to accent the ultima correctly without additional morphological information beyond the string value of the token.
