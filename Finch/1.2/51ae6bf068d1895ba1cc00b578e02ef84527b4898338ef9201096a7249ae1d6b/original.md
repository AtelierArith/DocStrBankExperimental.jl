```
@finch [options...] prgm
```

Run a finch program `prgm`. The syntax for a finch program is a set of nested loops, statements, and branches over pointwise array assignments. For example, the following program computes the sum of two arrays `A = B + C`:

```julia
@finch begin
    A .= 0
    for i = _
        A[i] = B[i] + C[i]
    end
    return A
end
```

Finch programs are composed using the following syntax:

  * `arr .= 0`: an array declaration initializing arr to zero.
  * `arr[inds...]`: an array access, the array must be a variable and each index may be another finch expression.
  * `x + y`, `f(x, y)`: function calls, where `x` and `y` are finch expressions.
  * `arr[inds...] = ex`: an array assignment expression, setting `arr[inds]` to the value of `ex`.
  * `arr[inds...] += ex`: an incrementing array expression, adding `ex` to `arr[inds]`. `*, &, |`, are supported.
  * `arr[inds...] <<min>>= ex`: a incrementing array expression with a custom operator, e.g. `<<min>>` is the minimum operator.
  * `for i = _ body end`: a loop over the index `i`, where `_` is computed from array access with `i` in `body`.
  * `if cond body end`: a conditional branch that executes only iterations where `cond` is true.
  * `return (tnss...,)`: at global scope, exit the program and return the tensors `tnss` with their new dimensions. By default, any tensor declared in global scope is returned.

Symbols are used to represent variables, and their values are taken from the environment. Loops introduce index variables into the scope of their bodies.

Finch uses the types of the arrays and symbolic analysis to discover program optimizations. If `B` and `C` are sparse array types, the program will only run over the nonzeros of either.

Semantically, Finch programs execute every iteration. However, Finch can use sparsity information to reliably skip iterations when possible.

`options` are optional keyword arguments:

  * `algebra`: the algebra to use for the program. The default is `DefaultAlgebra()`.
  * `mode`: the optimization mode to use for the program. Possible modes are:

      * `:debug`: run the program in debug mode, with bounds checking and better error handling.
      * `:safe`: run the program in safe mode, with modest checks for performance and correctness.
      * `:fast`: run the program in fast mode, with no checks or warnings, this mode is for power users.

    The default is `:safe`.

See also: [`@finch_code`](@ref)
