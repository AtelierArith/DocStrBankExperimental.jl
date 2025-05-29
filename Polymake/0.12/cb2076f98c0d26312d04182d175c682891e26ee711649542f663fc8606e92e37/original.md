```
@pm polymakeapp.function_name{Template, parameters}(args)
```

This macro can be used to

  * create `polymake` Big Objects (such as polytopes)
  * call `polymake` functions with specific template parameters.

The expression passed to the macro has to be:

  * a fully qualified name of a `polymake` object (i.e. starting with the

**lowercase** name of a polymake application), or

  * a function with template parameters enclosed in `{ ... }`.

# Examples

```jldoctest
julia> P = @pm polytope.Polytope{QuadraticExtension}(POINTS=[1 0 0; 0 1 0])
type: Polytope<QuadraticExtension<Rational>>

POINTS
1 0 0
0 1 0



julia> @pm common.convert_to{Float}(P)
type: Polytope<Float>

POINTS
1 0 0
0 1 0


CONE_AMBIENT_DIM
3



julia> @pm tropical.Polytope{Max}(POINTS=[1 0 0; 0 1 0])
type: Polytope<Max, Rational>

POINTS
0 -1 -1
0 1 0



```

!!! Note     the expression in `@pm` macro is parsed syntactically, so it has to be a valid `julia` expression. However template parameters **need not** to be defined in `julia`, but must be valid names of `polymake` property types. Nested types (such as `{QuadraticExtension{Rational}}`) are allowed.
