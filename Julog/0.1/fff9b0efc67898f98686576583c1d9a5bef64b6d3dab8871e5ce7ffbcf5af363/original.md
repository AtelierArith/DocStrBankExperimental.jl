```
@julog expr
```

Parse and return Julog expressions.

  * `@julog <term>` parses a Prolog-style term.
  * `@julog <term> <<= true` or `@julog <term>'` parses a fact (body-less clause).
  * `@julog <head> <<= <body>` parses a definite clause.
  * `@julog [<term|clause>, ...]` parses a vector of terms or clauses
  * `@julog <T>[<term>, ...]` parses to a vector of type `T` (e.g. `Const`)
  * `@julog list[<term>, ...]` parses a Prolog-style list directly to a term.

Additionally, the `$` operator can be used to interpolate regular Julia expressions as Julog constants, while the `:` operator can be used to interpolate variables referring to pre-constructed Julog terms into another Julog term or clause.
