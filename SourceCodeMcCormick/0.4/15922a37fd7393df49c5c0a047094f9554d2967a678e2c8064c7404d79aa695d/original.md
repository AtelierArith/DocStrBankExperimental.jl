```
convex_evaluator(::Num)
convex_evaluator(::Equation)
```

Given a symbolic expression or equation, return a function that evaluates the convex relaxation of the expression or the equation's right-hand side and a list of correctly ordered arguments to this new function. To get evaluator functions for {lower bound, upper bound, convex relaxation, concave relaxation}, use `all_evaluators`.

# Example

A representative use case is as follows:

```
@variables x, y
to_evaluate = 1 + x*y
evaluator, ordering = convex_evaluator(to_evaluate)
```

The same could be accomplished if `to_evaluate` were an Equation such as `0 ~ 1 + x*y`, although it is important to note that the left-hand side of such an equation is irrelevant for this function. In this example, the "ordering" object is now the vector `Num[xcc, xcv, xhi, xlo, ycc, ycv, yhi, ylo]`, indicating the correct arguments and argument order to give to `evaluator`. The names of these arguments are dependent on the variables used in the  `to_evaluate` expression and are, in general, the variable name(s) with an  appended `cv` and `cc` for the convex/concave values of the variables  (i.e., the point you wish to evaluate), `hi` for the variable's upper  bound, and `lo` for the variable's lower bound. Variables such as `x[1]`  will instead be represented as `x_1_cv` or equivalent. 

The expression's convex relaxation can now be evaluated at a specific point  `(x,y)` by setting `x = xcv = xcc` and `y = ycv = ycc`, and `x` and `y`'s upper and lower bounds to `xhi`, `yhi`, and `xlo`, `ylo`, respectively. E.g.,  to evaluate `to_evaluate`'s convex relaxation on the box `[0, 5]*[1, 3]` at the point `(2.5, 2)`, you can type: `evaluator(2.5, 2.5, 5.0, 0.0, 2.0, 2.0, 3.0, 1.0)`.

The `evaluator` function can also be broadcast, including over CuArrays. E.g., to evaluate the convex relaxation of the `to_evaluate` expression at 10,000 random points on the box `[0, 1]*[0, 1]` using a GPU, you could type:

```
x_cv = CUDA.rand(Float64, 10000)
x_cc = CUDA.rand(Float64, 10000)
x_hi = CUDA.ones(Float64, 10000)
x_lo = CUDA.zeros(Float64, 10000)
y_cv = CUDA.rand(Float64, 10000)
y_cc = CUDA.rand(Float64, 10000)
y_hi = CUDA.ones(Float64, 10000)
y_lo = CUDA.zeros(Float64, 10000)
out = evaluator.(x_cc, x_cv, x_hi, x_lo, y_cc, y_cv, y_hi, y_lo)
as_array = Array(out)
```
