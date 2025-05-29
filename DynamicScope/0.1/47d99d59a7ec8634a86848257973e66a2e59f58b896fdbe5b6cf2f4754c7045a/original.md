```
@dyn function name(...) ... end
```

Generates a macro `@name` that resolves default arguments and declared `@requires` in the calling scope.

Local variables that are provided by this function to inner dynamic functions should be declared with `@provides` to stop them from bubbling up. Function parameters are provided automatically.

The order of `@requires` and `@provides` matters, so that a function can both provide and declare a variable. For example in the case of `a=a+2`. The exception is that the first `@requires` overrides variables provided by function arguments. For example in the case of `function foo(a=a+2); @requires a`
