```
N = node(f::Function, args...)
```

Defines a `Node` object `N` wrapping a static operation `f` and arguments `args`. Each of the `n` elements of `args` must be a `Node` or `Source` object. The node `N` has the following calling behaviour:

```
N() = f(args[1](), args[2](), ..., args[n]())
N(rows=r) = f(args[1](rows=r), args[2](rows=r), ..., args[n](rows=r))
N(X) = f(args[1](X), args[2](X), ..., args[n](X))
```
