```
peelword(input::AbstractString)
```

Read the next 'word' from `input`. If `input` starts with a quote, this is the unescaped text between the opening and closing quote. Other wise this is simply the next word.

Returns a tuple of the form `(word, rest)`.

### Example

```julia-repl
julia> peelword("one two")
("one", "two")

julia> peelword(""one two" three")
("one two", "three")
```
