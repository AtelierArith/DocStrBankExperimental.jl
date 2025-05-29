```
TerminalProdArgument(argument)
```

`TerminalProdArgument` is a specialized wrapper structure. When used as an argument to the `prod` function, it returns itself without considering any product strategy  and does not perform any safety checks (e.g. `variate_form` or `support`). Attempting to calculate the product of two instances of `TerminalProdArgument` will raise an error.  Use `.argument` field to get the underlying wrapped argument.
