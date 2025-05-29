```
addmethod!(f, argtypes, ci)
```

Add a method to a function.

The types of the arguments is given as a `Tuple`.

Example:

```
g(x) = x + 13
ci = code_lowered(g)[1]
function f end
addmethod!(f, (Any,), ci)
f(1) # returns 14
```
