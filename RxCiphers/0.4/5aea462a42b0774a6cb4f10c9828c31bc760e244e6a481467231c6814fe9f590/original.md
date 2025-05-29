```
tokenise!(txt::Txt, dlm)
```

Tokenises `txt` in place, updating the `tokenised`, `frozen`, `is_tokenised`, `charspace` fields.

# Examples

```julia-repl
julia> t = Txt("Mr Wood moment")
14-character Txt:
"Mr Wood moment"

julia> tokenise!(t)
12-token Txt (Delimited Chars):
[1, 2, 3]

julia> t.is_tokenised
true
```
