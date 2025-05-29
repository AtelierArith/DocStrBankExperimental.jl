```
derivative_method(dref::DerivativeRef)::AbstractDerivativeMethod
```

Returns the evaluation method employed by `dref` that determines the numerical  computation scheme that will be used to evaluate the derivative. Note that this  is set on by the infinite parameter with respect to which the derivative is  defined.

**Example**

```julia-repl
julia> derivative_method(dref) 
FiniteDifference(Backward, true)
```
