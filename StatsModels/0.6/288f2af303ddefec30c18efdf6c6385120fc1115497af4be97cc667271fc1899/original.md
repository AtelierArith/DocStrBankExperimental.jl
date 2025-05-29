```
@formula(ex)
```

Capture and parse a formula expression as a `Formula` struct.

A formula is an abstract specification of a dependence between *left-hand* and *right-hand* side variables as in, e.g., a regression model.  Each side specifies at a high level how tabular data is to be converted to a numerical matrix suitable for modeling.  This specification looks something like Julia code, is represented as a Julia `Expr`, but uses special syntax.  The `@formula` macro takes an expression like `y ~ 1 + a*b`, transforms it according to the formula syntax rules into a lowered form (like `y ~ 1 + a + b + a&b`), and constructs a `Formula` struct which captures the original expression, the lowered expression, and the left- and right-hand-side.

Operators that have special interpretations in this syntax are

  * `~` is the formula separator, where it is a binary operator (the first argument is the left-hand side, and the second is the right-hand side.
  * `+` concatenates variables as columns when generating a model matrix.
  * `&` representes an *interaction* between two or more variables, which corresponds to a row-wise kronecker product of the individual terms (or element-wise product if all terms involved are continuous/scalar).
  * `*` expands to all main effects and interactions: `a*b` is equivalent to `a+b+a&b`, `a*b*c` to `a+b+c+a&b+a&c+b&c+a&b&c`, etc.
  * `1`, `0`, and `-1` indicate the presence (for `1`) or absence (for `0` and `-1`) of an intercept column.

The rules that are applied are

  * The associative rule (un-nests nested calls to `+`, `&`, and `*`).
  * The distributive rule (interactions `&` distribute over concatenation `+`).
  * The `*` rule expands `a*b` to `a+b+a&b` (recursively).
  * Subtraction is converted to addition and negation, so `x-1` becomes `x + -1` (applies only to subtraction of literal 1).
  * Single-argument `&` calls are stripped, so `&(x)` becomes the main effect `x`.
