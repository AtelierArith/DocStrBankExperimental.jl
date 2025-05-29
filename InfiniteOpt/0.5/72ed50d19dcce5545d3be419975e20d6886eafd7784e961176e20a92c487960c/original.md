```
@register(model::InfiniteModel, func_expr, [gradient::Function], [hessian::Function])
```

Register a user-defined function in accordance with `func_expr` such that it can  be used in `NLPExpr`s that are used with `model` without being traced.

**Argument Information** Here `func_expr` is of the form: `myfunc(a, b)` where `myfunc` is the function  name and the number of arguments are given symbolically. Note that the choice  of argument symbols is arbitrary. Each function argument must support anything  of type `Real` to specified.

Here we can also specify a gradient function `gradient` which for 1 argument  functions must taken in the 1 argument and return its derivative. For  multi-argument functions the gradient function must be of the form:

```julia
function gradient(g::AbstractVector{T}, args::T...) where {T <: Real}
    # fill g vector with the gradient of the function
end
```

For 1 argument functions we can also specify a hessian function with takes that  argument and return the 2nd derivative. Hessians can ge specified for  multi-argument functions, but `JuMP` backends do not currently support this.

If no gradient and/or hessian is given, the automatic differentation capabilities  of the backend (e.g., `JuMP`) will be used to determine them. Note that the  `JuMP` backend does not use Hessian's for user-defined multi-argument functions.

**Notes**

  * When possible, tracing is preferred over registering a function (see  [Function Tracing](@ref) for more info).
  * Only user-defined functions can be specified. If the function is used by a  package then it can not be used directly. However, we can readily wrap it in a  new function `newfunc(a) = pkgfunc(a)`.
  * We can only register functions in the same scope that they are defined in.
  * Registered functions can only be used in or below the scope in which they are  registered. For instance, if we register some function inside of another  function then we can only use it inside that function (not outside of it).
  * A function with a given name and number of arguments can only be registered  once in a particular model.

**Examples**

```julia-repl
julia> @variable(model, x)
x

julia> f(a) = a^3;

julia> f(x) # user-function gets traced
x^3

julia> @register(model, f(a)) # register function
f (generic function with 2 methods)

julia> f(x) # function is no longer traced and autodifferentiation will be used
f(x)

julia> f2(a) = a^2; g2(a) = 2 * a; h2(a) = 2;

julia> @register(model, f2(a), g2, h2) # register with explicit gradient and hessian
f2 (generic function with 2 methods)

julia> f2(x)
f2(x)

julia> f3(a, b) = a * b^2;

julia> function g3(v, a, b)
          v[1] = b^2
          v[2] = 2 * a * b
          return
       end;

julia> @register(model, f3(a, b), g3) # register multi-argument function
f3 (generic function with 4 methods)

julia> f3(42, x)
f3(42, x)
```
