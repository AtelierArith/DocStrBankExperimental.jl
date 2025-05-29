```
struct Alphabet{A,I}
    characters::Vector{A}
    char_to_index::Dict{A, I}
    index_to_char::Dict{I, A}
    default_char = nothing
    default_index
end
```

Structure allowing the mapping from biological symbols of type `A` to integers of type `I`.     The typical use case would be `Alphabet{Char, Int}`. `Alphabet` can be constructed

  * from a `Vector` of symbols and an optional type `I`, *e.g.* `Alphabet(['A','C','G','T'], UInt8)::Alphabet{Char, UInt8}`
  * from a `String` and an optional type, *e.g.* `Alphabet("ACGT")`
  * from a mapping `Dict{A, I}` where `I<:Integer`: `Alphabet(Dict('A'=>1, 'C'=>2))`
  * from a `Symbol`, using default alphabets, *e.g.* `Alphabet(:nt)`
  * from an integer, using default alphabets (see `?default_alphabets`).
