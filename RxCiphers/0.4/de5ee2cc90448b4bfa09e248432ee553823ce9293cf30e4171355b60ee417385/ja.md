```
nchar(txt::Txt, n::Int) -> Txt
```

`txt`を`n`文字のサブストリングで再トークン化し、順序`N = n`の`NCharSpace{N}`を割り当てます。もし`txt.charspace`の順序が1より大きい場合、最初にテキストが減少されます（`reduce(txt)`）。

# 例

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
