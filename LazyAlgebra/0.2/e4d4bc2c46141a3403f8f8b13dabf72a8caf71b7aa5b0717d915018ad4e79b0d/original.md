```
Identity()
```

yields the identity linear mapping. The purpose of this mapping is to be as efficient as possible, hence the result of applying this mapping may be the same as the input argument.

The identity is a singleton and is also available as:

```
Id
```

The `LinearAlgebra` module of the standard library exports a constant `I` which also corresponds to the identity (but in the sense of a matrix). When `I` is combined with any LazyAlgebra mapping, it is recognized as an alias of `Id`. So that, for instance, `I/A`, `A\I`, `Id/A` and `A\Id` all yield `inv(A)` for any LazyAlgebra mappings `A`.
