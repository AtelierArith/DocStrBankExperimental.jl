Split string `s` into an Array of strings representing syllables.

```julia
syllabify(s, ortho)

```

# Example

```jldoctest
syllables = PolytonicGreek.syllabify("κελεύει")
join(syllables, "-")
"κε-λευ-ει"
```
