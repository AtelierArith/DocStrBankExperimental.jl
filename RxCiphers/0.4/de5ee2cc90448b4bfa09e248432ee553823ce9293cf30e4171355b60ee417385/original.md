```
nchar(txt::Txt, n::Int) -> Txt
```

Retokenises `txt` with `n` character substrings, assigning a `NCharSpace{N}` of order `N = n`. If `txt.charspace` has order greater than 1, first the text is reduced (`reduce(txt)`).

# Examples

```julia-repl
julia> example
24-character Txt:
"Literally George Orwell."

julia> tokenise!(example)
21-token Txt:
[12, 9, 20, 5, 18, 1, 12, 12, 25, 7  …  15, 18, 7, 5, 15, 18, 23, 5, 12, 12]

julia> nexample = nchar(example, 3)
7-token Txt (3-gram tokens):
[13064, 447, 16522, 9575, 2878, 15329, 7727]

julia> untokenise(nexample[1], nexample.charspace)
"LIT"
```
