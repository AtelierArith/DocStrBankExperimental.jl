```
@chain(initial_value, block::Expr)
```

Rewrites a block expression to feed the result of each line into the next one. The initial value is given by the first argument.

In all lines, underscores are replaced by the previous line's result. If there are no underscores and the expression is a symbol, the symbol is rewritten to a function call with the previous result as the only argument. If there are no underscores and the expression is a function call or a macrocall, the call has the previous result prepended as the first argument.

Example:

```
x = @chain [1, 2, 3] begin
    filter(!=(2), _)
    sqrt.(_)
    sum
end
x == sum(sqrt.(filter(!=(2), [1, 2, 3])))
```
