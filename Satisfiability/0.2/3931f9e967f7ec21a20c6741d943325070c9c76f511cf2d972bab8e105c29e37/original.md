```
smt(z::AbstractExpr)
smt(z1,...,zn; assert=true)
smt([z1,...,zn]; assert=true, line_ending='
```

', as_list=true)

Generate the SMT representation of `z` or `and(z1,...,zn)`.

When calling `smt([z1,...,zn])`, the array must have type `Array{AbstractExpr}`. Note that list comprehensions do not preserve array typing. For example, if `z` is an array of `BoolExpr`, `[z[i] for i=1:n]` will be an array of type `Any`. To preserve the correct type, use `BoolExpr[z[i] for i=1:n]`.

Optional keyword arguments are:

1. `assert = true|false`: default `true`. Whether to generate the (assert ...) SMT-LIB statement, which asserts that an expression must be true. This option is only valid if `smt` is called on a Boolean expression.
2. `line_ending`: If not set, this defaults to "

" on Windows and ' ' everywhere else.

3. `as_list = true|false`: default `false`. When `true`, `smt` returns a list of commands instead of a single `line_ending`-separated string.
