```
@espy function ... end
```

From an anotated function code, generate     - "clean" code, in which the anotations have been deleted, and with        the call syntax `argout... = foo(argin...)`     - "espying" code, with added input and ouput arguments       `argout...,res = foo(argin...,req)` where `req` has been       generated using `@request` and `res` is a nested structure       of `NamedTuple`s and `NTuple`s containing the requested data.

The macro is not general: it is designed for `residual` and `lagrangian`, which for performance have to be programmed in "immutable" style: they must never mutate variables (this implies in particular, no adding into an array in a loop over Gauss points). So @espy only supports the specific programming constructs needed in this style.

The following is an example of anotated code:

```
@espy function residual(x::Vector{R},y) where{R<:Real}
    ngp=2
    accum = ntuple(ngp) do igp
        ☼z = x[igp]+y[igp]
        ☼s,☼t  = ☼material(z)
        ♢square = s^2
        @named(s) 
    end
    r = sum(i->accum[i].s,ngp)
    return r,nothing,nothing
end
```

  * The keyword `function` is preceded by the macro-call `@espy`.
  * The name of requestable variables is preceded by `☼` (`\sun`).  Such anotation must always appear on the left of an assigment.
  * If the name of a variable is preceded by `♢` (`\diamond`), then the variable is evaluated only if requested. Such a notation can only be used if there is only one variable left of the assignement.
  * The name of a function being called must be preceded by `☼` if the definition of the function is itself preceeded by the macro-call `@espy`.
  * `for`-loops are not supported. `do`-loops must be used: to be efficient,  `residual` and `lagrangian` must not allocate and thus use immutables.
  * The keyword `return` must be explicitly used, and if must be followed the a comma separated list of output variables. Syntaxes like `return if...` are not supported.

See also: [`@request`](@ref), [`@espydbg`](@ref), [`getresult`](@ref)
