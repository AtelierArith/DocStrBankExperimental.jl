```
@chain(initial_value, args...)
```

Rewrites a series of argments, either expressions or symbols, to feed the result of each line into the next one. The initial value is given by the first argument.

In all arguments, underscores are replaced by the argument's result. If there are no underscores and the argument is a symbol, the symbol is rewritten to a function call with the previous result as the only argument. If there are no underscores and the argument is a function call or a macrocall, the call has the previous result prepended as the first argument.

Example:

```
x = @chain [1, 2, 3] filter(!=(2), _) sqrt.(_) sum

x == sum(sqrt.(filter(!=(2), [1, 2, 3])))
```
