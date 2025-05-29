```
peggy(expr...; whitespace=r"[[:space:]]*")
```

Create a `Parser` from a PEG expression.

The parser matches each expr sequentiallly and returns the combined results (details below).

Each expr can be one of the following.

  * `String` - matches & yields the string literal
  * `Regex` - matches the `Regex` and yields the match value (but avoid this)
  * `Symbol` - matches to expression associated with the symbol in a [`grammar`](@ref).
  * `Symbol => expr` - matches `expr` and assign it a names.
  * `expr => callable` - matches `expr` and yields result of applying `callable` to its value.
  * `peg_epxr => k` - short-hand for `expr` => _ -> k`
  * `(expr, exprs...)` - same as `peggy(expr, exprs...)`
  * `[expr, exprs...]` - same as `many(expr, exprs; max=1)`
  * `Parser` - any expression that yields a parser

# Names and sequence results

Each element of a sequence has a name.  `Symbol` and `Symbol => expr` take the name of the symbol. All other expressions are named ":_". The value of the sequence is then formed as follows.

Discard values with names starting with "_" if there are any that do not.  If a single value remains, that is the sequence value. Othewise the value is a `Vector` of the remaining values.

# Whitespace

String literals by default ignore surrounding whitespace.  Use option `whitespace=r""` to disable this.
