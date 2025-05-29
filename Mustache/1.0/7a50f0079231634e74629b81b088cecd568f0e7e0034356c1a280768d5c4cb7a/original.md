```
jmt"string"
```

String macro that interpolates values escaped by dollar signs, then parses strings.

Note: modified from a macro in [HypertextLiteral](https://github.com/clarkevans/HypertextLiteral.jl/blob/master/src/macros.jl).

Example:

```
x = 1
toks = jmt"$(2x) by {{:a}}"
toks(; a=2) # "2 by 2"
```
