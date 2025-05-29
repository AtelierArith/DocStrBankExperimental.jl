```
PolyForm{T} <: Symbolic
```

Abstracts a [MultivariatePolynomials.jl](https://juliaalgebra.github.io/MultivariatePolynomials.jl/stable/) as a SymbolicUtils expression and vice-versa.

The SymbolicUtils term interface (`isexpr`/`iscall`, `operation, and`arguments`) works on PolyForm lazily: the`operation`and`arguments`are created by converting one level of arguments into SymbolicUtils expressions. They may further contain PolyForm within them. We use this to hold polynomials in memory while doing`simplify_fractions`.

```
PolyForm{T}(x; Fs=Union{typeof(*),typeof(+),typeof(^)}, recurse=false)
```

Turn a Symbolic expression `x` into a polynomial and return a PolyForm that abstracts it.

`Fs` are the types of functions which should be applied if arguments are themselves polynomialized. For example, if you only want to polynomialize the base of power expressions, you would  leave out `typeof(^)` from the union. In this case `^` is not called, but maintained as a `Pow` term.

`recurse` is a flag which calls `PolyForm` recursively on subexpressions. For example:

```julia
PolyForm(sin((x+y)^2))               #=> sin((x+y)^2)
PolyForm(sin((x+y)^2), recurse=true) #=> sin((x^2 + (2x)y + y^2))
```
