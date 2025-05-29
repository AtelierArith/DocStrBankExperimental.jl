```
DiagonalAndreiModel(nlp; d0 = fill!(S(undef, nlp.meta.nvar), 1.0))
```

Construct a `DiagonalAndreiModel` from another type of nlp, in which the Hessian is approximated via a diagonal Andrei quasi-Newton operator. `d0` is the initial approximation of the diagonal of the Hessian, and by default a vector of ones. See the [`DiagonalAndrei operator documentation`](https://juliasmoothoptimizers.github.io/LinearOperators.jl/stable/reference/#LinearOperators.DiagonalAndrei).
