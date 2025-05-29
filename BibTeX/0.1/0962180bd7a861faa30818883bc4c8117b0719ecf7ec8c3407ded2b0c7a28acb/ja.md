```
parse_bibtex(text)
```

これはBibTexのためのシンプルな入力パーサーです。標準仕様を見つけるのに苦労しましたが、実際のBibTexのいくつかの機能を含めました。前文（または空の文字列）と辞書の辞書を返します。

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
