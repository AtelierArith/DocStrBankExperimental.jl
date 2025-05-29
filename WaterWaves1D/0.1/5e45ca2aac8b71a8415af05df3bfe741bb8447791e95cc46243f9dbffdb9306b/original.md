```
EulerSymp(arguments;Niter,implicit,realdata)
```

Symplectic Euler solver. The implicit Euler method is first used on one equation, then the explicit Euler method is used on the second one. The implicit equation is solved via Neumann iteration

Construct an object of type `TimeSolver` to be used in `Problem(model, initial, param; solver::TimeSolver)`

Arguments can be either

0. an object of type `AbstractModel`;
1. an `Array` of size `(N,2)` where `N` is the number of collocation points;
2. a `NamedTuple` containing a key `N`.

The keyword argument `Niter` (optional, defaut value = 10) determines the number of steps in the Neumann iteration solver of the implicit step. The keyword argument `implicit` (optional, defaut value = 1) determines which equation is implicit (must be `1` or `2`). The keyword argument `realdata` is optional, and determines whether pre-allocated vectors are real- or complex-valued. By default, they are either determined by the model or the type of the array in case `0.` and `1.`, complex-valued in case `2.`.
