```
Pattern syntactic sugar
```

the logical operators `|`, `&`, and `~`  may be applied to all kind of `Pattern`s with the usual meaning.

  * `~` : unary negation operator - pattern does not match (highest priority)
  * `&` : binary logical and - both patterns match
  * `|` : binary logical or - any of the pattern match (lowest priority)
  * parentheses can be used to overrule operator precedence.
  * `[p...]` is the same as `p[1] | p[2] ...`
  * `(p...)` is the same as `p[1] & p[2] ...`
  * `~(p...) === ~((p...))` - that is `~(p[1] & p[2] ...)`
  * Precedence of '*' is higher that `~` for character and string objects:

so `~ "a" * "b"  === ~("a" * "b") === ~"ab"`  also `~'a'^2*"b" === ~"aab"`
