`toexpr(c::Context, t) -> Any`

Converts GATlab syntax into an Expr that can be read in via `fromexpr` to get the same thing. Crucially, the output of this will depend on the order of the scopes in `c`, and if read back in with a different `c` may end up with different results.
