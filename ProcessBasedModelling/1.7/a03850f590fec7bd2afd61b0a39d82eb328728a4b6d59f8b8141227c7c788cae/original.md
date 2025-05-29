```
@convert_to_parameters vars...
```

Convert all variables `vars` into `@parameters` with name the same as `vars` and default value the same as the value of `vars`. The macro leaves unaltered inputs that are of type `Num`, assumming they are already parameters. It also replaces [`LiteralParameter`](@ref) inputs with its literal values. This macro is extremely useful to convert e.g., keyword arguments into named parameters, while also allowing the user to give custom parameter names, or to leave some keywords as numeric literals.

Example:

```
julia> A, B = 0.5, 0.5
(0.5, 0.5)

julia> C = first(@parameters X = 0.5)

julia> @convert_to_parameters A B C
3-element Vector{Num}:
 A
 B
 X

julia> typeof(A) # `A` is not a number anymore!
Num

julia> default_value(A)
0.5

julia> C # the binding `C` still corresponds to parameter named `:X`!
 X
```
