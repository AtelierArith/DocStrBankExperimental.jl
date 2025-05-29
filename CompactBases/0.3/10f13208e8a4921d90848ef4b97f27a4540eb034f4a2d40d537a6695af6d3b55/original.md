```
DiagonalOperator
```

Helper structure that when acting on a function $f(x)$ produces the product $f(x)g(x)$, where $g(x)$ is e.g. a potential. This is similar to `R'*QuasiDiagonal(g.(x))*R` in intent, but simplifies the case when $g(x)$ needs to be updated, without computing a lot overlap integrals. This is accomplished by computing the [`FunctionProduct`](@ref) of the two functions directly.
