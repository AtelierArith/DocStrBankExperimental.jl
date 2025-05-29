```
parse_bibtex(text)
```

This is a simple input parser for BibTex. I had trouble finding a standard specification, but I've included several features of real BibTex. Returns a preamble (or an empty string) and a dict of dicts.

```jldoctest
julia> using BibTeX

julia> preamble, result = parse_bibtex("""
            @preamble{some instructions}
            @comment blah blah
            @string{short = long}
            @a{b,
              c = { {c} c},
              d = "d d",
              e = f # short
            }
            """);

julia> preamble
"some instructions"

julia> result["b"]["type"]
"a"

julia> result["b"]["c"]
"{ c } c"

julia> result["b"]["d"]
"d d"

julia> result["b"]["e"]
"f short"

julia> parse_bibtex("@book")
ERROR: Expected { on line 1
[...]

julia> parse_bibtex("@book@")
ERROR: Expected { on line 1
[...]
```
