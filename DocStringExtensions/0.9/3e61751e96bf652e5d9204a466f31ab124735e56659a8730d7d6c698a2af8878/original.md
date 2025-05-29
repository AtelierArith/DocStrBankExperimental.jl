An [`Abbreviation`](@ref) for including a simplified representation of all the method signatures with types that match the given docstring. See [`printmethod`](@ref) for details on the simplifications that are applied.

# Examples

The generated markdown text will look similar to the following example where a function `f` defines method taking two positional arguments, `x` and `y`, and two keywords, `a` and the `b`.

````markdown
```julia
f(x::Int, y::Int; a, b...)
```
````
