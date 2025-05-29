```
RK4(arguments;realdata)
```

Explicit Runge-Kutta fourth order solver.

Construct an object of type `TimeSolver` to be used in `Problem(model, initial, param; solver::TimeSolver)`

Arguments can be either

0. an object of type `AbstractModel`, typically the model you will solve with the solver;
1. an `Array` of size `(N,datasize)` where `N` is the number of collocation points and `datasize` the number of equations solved;
2. `(param,datasize)` where `param` is a `NamedTuple` containing a key `N`, and `datasize` a integer (optional, by default `datasize=2`).

The keyword argument `realdata` is optional, and determines whether pre-allocated vectors are real- or complex-valued. By default, they are either determined by the model or the type of the array in case `0.` and `1.`, complex-valued in case `2.`.
