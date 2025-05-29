```
expr2csgrammar(ex::Expr)::ContextSensitiveGrammar
```

A function for converting an `Expr` to a [`ContextSensitiveGrammar`](@ref). If the expression is hardcoded, you should use the [`@csgrammar`](@ref) macro. Only expressions in the correct format (see [`@csgrammar`](@ref)) can be converted.

### Example usage:

```@example
grammar = expr2csgrammar(
	begin
		R = x
		R = 1 | 2
		R = R + R
	end
)
```
