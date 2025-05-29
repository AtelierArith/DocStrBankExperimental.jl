```
expr2pcsgrammar(ex::Expr)::ContextSensitiveGrammar
```

Function for converting an `Expr` to a [`ContextSensitiveGrammar`](@ref) with probabilities. If the expression is hardcoded, you should use the `@pcsgrammar` macro. Only expressions in the correct format (see [`@pcsgrammar`](@ref)) can be converted.

### Example usage:

```@example
grammar = expr2pcsgrammar(
	begin
		0.5 : R = x
		0.3 : R = 1 | 2
		0.2 : R = R + R
	end
)
```
