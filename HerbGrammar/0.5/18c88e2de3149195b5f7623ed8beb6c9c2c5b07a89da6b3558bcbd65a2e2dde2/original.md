```
@csgrammar
```

A macro for defining a [`ContextSensitiveGrammar`](@ref).  AbstractConstraints can be added afterwards using the [`addconstraint!`](@ref) function.

### Example usage:

```julia
grammar = @csgrammar begin
	R = x
	R = 1 | 2
	R = R + R
end
```

### Syntax:

  * Literals: Symbols that are already defined in Julia are considered literals, such as `1`, `2`, or `π`. For example: `R = 1`.
  * Variables: A variable is a symbol that is not a nonterminal symbol and not already defined in Julia. For example: `R = x`.
  * Functions: Functions and infix operators that are defined in Julia or the `Main` module can be used  with the default evaluator. For example: `R = R + R`, `R = f(a, b)`.
  * Combinations: Multiple rules can be defined on a single line in the grammar definition using the `|` symbol. For example: `R = 1 | 2 | 3`.
  * Iterators: Another way to define multiple rules is by providing a Julia iterator after a `|` symbol. For example: `R = |(1:9)`.

### Related:

  * [`@pcsgrammar`](@ref) uses a similar syntax to create probabilistic [`ContextSensitiveGrammar`](@ref)s.
