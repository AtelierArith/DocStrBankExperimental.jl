```
grad(::Num; force::Bool)
grad(::Num, ::Vector{Num}; base_level::Bool, force::Bool)
```

Given a symbolic expression, return vectors of expressions representing the subgradients of the convex and concave relaxations. Inputs are the expression that subgradients are requested for and, optionally, the dimensions that are needed. If no `Vector{Num}` is given, subgradients will be produced with respect to all variables found in the expression.

By default, `grad` will assume that the input is a subexpression which is part of a larger expression that subgradients are desired for. Therefore, values for the gradients will be required as inputs to the created functions. Alternatively, if `base_level` is set to `true`, gradients will be constructed of `0`s and a `1` based on the order of variables given in the `Vector{Num}`.

This function includes a check to make sure excessively large substitutions are not being made, which can stall Julia for  potentially long time period. If large substitutions are detected, `grad` will back out of calculations and warn the user. This functionality can be suppressed by setting `force=true`.

# Example

```
cvgrad, ccgrad = grad(x*y, [x,y,z], base_level=true);
```

Here, subgradients are requested for the expression `x*y`. The user has indicated that the full expression being considered is 3-dimensional, with dimensions `[x,y,z]`, so the resulting gradient expressions will also be 3-dimensional. E.g., `cvgrad` will be a 3-element Vector{Num} with elements `cvgrad[1]` being the x-component of the subgradient of  the convex relaxation of `x*y`, `cvgrad[2]` being the y-component, and `cvgrad[3]` being the z-component. Because `base_level` has been set to `true`, the gradients of `x`, `y`, and `z` are internally set to `[1,0,0]`, `[0,1,0]`, and `[0,0,1]`, respectively, prior to creating the subgradient expressions for the convex relaxation of `x*y`. Note  that all of the above also applies to `ccgrad`, which contains the  subgradients of the concave relaxation of the input expression. 

If `base_level` were not set to `true` (and instead retained its default value of `false`), the resulting subgradient expressions would be functions of `[dx/dx, dx/dy, dx/dz]`, `[dy/dx, dy/dy, dy/dz]`, and `[dz/dx, dz/dy, dz/dz]`, respectively. This may be important if expressions are broken into subexpressions that are individually fed to `grad`. E.g.,:

```
cvgrad, ccgrad = grad(a*b, [x,y,z])
```

In this case, `a` and `b` may be composite, intermediate terms, which contain the base-level variables `x`, `y`, and `z`. The resulting expressions from this call of `grad` would then require inputs of the McCormick tuples of `a` and `b`,  as well as values for `[da/dx, da/dy, da/dz]` and `[db/dx, db/dy, db/dz]`. 

If `grad` is called with only the first argument, `base_level` will be assumed to be `true` (i.e., it is assumed that if the user is writing an expression and wants only the variables present in the expression to be used in the creation of subgradient expressions, the expression is likely made only of base-level variables).
