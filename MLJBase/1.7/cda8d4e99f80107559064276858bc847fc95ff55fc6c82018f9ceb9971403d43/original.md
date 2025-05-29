```
J = node(f, mach::Machine, args...)
```

Defines a dynamic `Node` object `J` wrapping a dynamic operation `f` (`predict`, `predict_mean`, `transform`, etc), a nodal machine `mach` and arguments `args`. Its calling behaviour, which depends on the outcome of training `mach` (and, implicitly, on training outcomes affecting its arguments) is this:

```
J() = f(mach, args[1](), args[2](), ..., args[n]())
J(rows=r) = f(mach, args[1](rows=r), args[2](rows=r), ..., args[n](rows=r))
J(X) = f(mach, args[1](X), args[2](X), ..., args[n](X))
```

Generally `n=1` or `n=2` in this latter case.

```
predict(mach, X::AbsractNode, y::AbstractNode)
predict_mean(mach, X::AbstractNode, y::AbstractNode)
predict_median(mach, X::AbstractNode, y::AbstractNode)
predict_mode(mach, X::AbstractNode, y::AbstractNode)
transform(mach, X::AbstractNode)
inverse_transform(mach, X::AbstractNode)
```

Shortcuts for `J = node(predict, mach, X, y)`, etc.

Calling a node is a recursive operation which terminates in the call to a source node (or nodes). Calling nodes on *new* data `X` fails unless the number of such nodes is one.

See also: [`Node`](@ref), [`@node`](@ref), [`source`](@ref), [`origins`](@ref).
