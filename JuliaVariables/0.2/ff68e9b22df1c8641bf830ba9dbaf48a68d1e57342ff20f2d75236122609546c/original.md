Process expressions with returning their scope. The `solve!` function can only accept ASTs that satifies following conditions:

  * It's a *simplified* expression, which means `JuliaVariables.simplify_ex` will have no effects on the expression. You can check the very concise code of `JuliaVariables.simplify_ex` to understand the simplification rules.
  * No macros included in the expression, as we don't know how much a macro could change the code.
