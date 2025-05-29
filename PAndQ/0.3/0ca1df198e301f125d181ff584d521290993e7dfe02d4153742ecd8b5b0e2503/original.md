```
@atomize(x)
```

Instantiate constants and variables inline.

Constants are instantiated with the `$` interpolation syntax. Variables are instantiated with previously undefined symbols.

!!! warning
    This macro attempts to ignore symbols that are being assigned a value. For example, `@atomize f(; x = p) = x ∧ q` should be equivalent to `f(; x = @atomize p) = x ∧ @atomize q`. However, this feature is in-progress and only works in some cases. The implementation is cautious to skip the parts of the expression that it cannot yet handle.


# Examples

```jldoctest
julia> @atomize x = p ∧ q
p ∧ q

julia> @atomize x → r
(p ∧ q) → r

julia> @atomize $1 ∧ $(1 + 1)
$(1) ∧ $(2)
```
