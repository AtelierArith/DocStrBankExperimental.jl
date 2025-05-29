```
@Compute(...)
```

The `@Compute` macro returns a function which performs a calculation on the properties of an object, such as a `NamedTuple`.

The input expression is standard Julia code, with `$` prepended to property names. For example. if you want to refer to a property named `a` then use `$a` in the expression.

# Example

```julia
julia> nt = (a = 1, b = 2.0, c = false)
(a = 1, b = 2.0, c = false)

julia> @Compute($a + $b)(nt)
3.0
```
