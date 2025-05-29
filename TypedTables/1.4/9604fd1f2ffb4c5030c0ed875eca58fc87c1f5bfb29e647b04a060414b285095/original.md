```
@Select(...)
```

The `@Select` macro returns a function which performs an arbitrary transformation of the properties of an object, such as a `NamedTuple`.

The input expression is a comma-seperated list of `lhs = rhs` pairs. The `lhs` is the name of the new property to calculate. The `rhs is  standard Julia code, with`:(` prepended to input property names. For example. if you want to rename an input property `)a`to be called`b`, use`@Select(b = :a)`.

As a special case, if a property is to be simply replicated the `= rhs` part can be dropped, for example `@Select(a)` is synomous with `@Select(a = $a)`.

# Example

```julia
julia> nt = (a = 1, b = 2.0, c = false)
(a = 1, b = 2.0, c = false)

julia> @Select(a, sum_a_b = $a + $b)(nt)
(a = 1, sum_a_b = 3.0)
```
