```
LaSROptions(;kws...)
```

これはLibraryAugmentedSymbolicRegressionモジュールのオプションを定義します。これは、LLMOptionsとSymbolicRegression.Optionsの両方を含む合成型です。

# 引数

  * `llm_options::LLMOptions`: LLM推論のためのオプション。
  * `sr_options::SymbolicRegression.Options`: SymbolicRegressionモジュールのためのオプション。

# 例

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
