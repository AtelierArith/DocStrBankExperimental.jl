`family_imprimitive(S)`

`S` should be a symbol for a unipotent characters of an imprimitive complex reflection  group 'G(e,1,n)' or 'G(e,e,n)'. The function returns the family containing `S`.

```julia-repl
julia> family_imprimitive([[0,1],[1],[0]])
Family(0011,cospecial=2)
imprimitive family
┌─────┬──────────────────────────────┐
│label│eigen      1        2        3│
├─────┼──────────────────────────────┤
│1    │  ζ₃²  √-3/3   -√-3/3    √-3/3│
│2    │    1 -√-3/3 ζ₃²√-3/3 -ζ₃√-3/3│
│3    │    1  √-3/3 -ζ₃√-3/3 ζ₃²√-3/3│
└─────┴──────────────────────────────┘
```
