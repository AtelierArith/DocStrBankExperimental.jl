```
@pcsgrammar
```

A macro for defining a probabilistic [`ContextSensitiveGrammar`](@ref). 

### Example usage:

```julia
grammar = @pcsgrammar begin
	0.5 : R = x
	0.3 : R = 1 | 2
	0.2 : R = R + R
end
```

### Syntax:

The syntax of rules is identical to the syntax used by [`@csgrammar`](@ref):

  * Literals: Symbols that are already defined in Julia are considered literals, such as `1`, `2`, or `π`. For example: `R = 1`.
  * Variables: A variable is a symbol that is not a nonterminal symbol and not already defined in Julia. For example: `R = x`.
  * Functions: Functions and infix operators that are defined in Julia or the `Main` module can be used  with the default evaluator. For example: `R = R + R`, `R = f(a, b)`.
  * Combinations: Multiple rules can be defined on a single line in the grammar definition using the `|` symbol. For example: `R = 1 | 2 | 3`.
  * Iterators: Another way to define multiple rules is by providing a Julia iterator after a `|` symbol. For example: `R = |(1:9)`.

Every rule is also prefixed with a probability. Rules and probabilities are separated using the `:` symbol. If multiple rules are defined on a single line, the probability is equally divided between the rules. The sum of probabilities for all rules of a certain non-terminal symbol should be equal to 1.  The probabilities are automatically scaled if this isn't the case.

### Related:

  * [`@csgrammar`](@ref) uses a similar syntax to create non-probabilistic [`ContextSensitiveGrammar`](@ref)s.
