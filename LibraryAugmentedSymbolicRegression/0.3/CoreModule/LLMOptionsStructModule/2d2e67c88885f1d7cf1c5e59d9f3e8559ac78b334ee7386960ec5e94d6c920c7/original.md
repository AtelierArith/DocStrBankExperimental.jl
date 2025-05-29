```
LaSROptions(;kws...)
```

This defines the options for the LibraryAugmentedSymbolicRegression module. It is a composite type that contains both the LLMOptions and the SymbolicRegression.Options.

# Arguments

  * `llm_options::LLMOptions`: Options for the LLM inference.
  * `sr_options::SymbolicRegression.Options`: Options for the SymbolicRegression module.

# Example

```julia
llm_options = LLMOptions(;
    ...
)

options = Options(;
    binary_operators = (+, *, -, /, ^),
    unary_operators = (cos, log),
    nested_constraints = [(^) => [(^) => 0, cos => 0, log => 0], (/) => [(/) => 1], (cos) => [cos => 0, log => 0], log => [log => 0, cos => 0, (^) => 0]],
    constraints = [(^) => (3, 1), log => 5, cos => 7],
    populations=20,
)

lasr_options = LaSROptions(llm_options, options)
```
