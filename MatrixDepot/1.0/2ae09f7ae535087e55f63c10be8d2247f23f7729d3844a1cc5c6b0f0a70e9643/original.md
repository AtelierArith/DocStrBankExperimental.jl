```
mdlist([db,] p::Pattern)
```

return a vector of full matrix names where name or alias match given pattern. `p` can be one of the following:

  * a plain string (without characters `*` and `?`) which must match exactly
  * a string containing `*` and `?` acting like a shell path pattern
  * a regular expression
  * an integer matching equivalent to the alias string `"#$p"`
  * a range of integers
  * a group name expressed as a symbol e.g. `:local`, `:all`, `:illcond`, `:posdef`
  * the name of a predicate function `f(::MatrixData)::Bool`, e.g. `issymmetric`, isposdef, ...
  * a vector of patterns meaning the union (or `|`)
  * a tuple of patterns meaning the intersection ( or `&`)
