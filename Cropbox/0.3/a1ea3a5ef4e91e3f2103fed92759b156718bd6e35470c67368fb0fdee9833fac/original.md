```
@look ex
@look s[, k]
```

Macro version of `look` supports a convenient way of accessing variable without relying on symbol. Both `@look s.a` and `@look s a` work the same as `look(s, :a)`.

See also: [`look`](@ref)

# Examples

```julia-repl
julia> "my system"
       @system S(Controller) begin
           "a param"
           a => 1 ~ preserve(parameter)
       end;

julia> @look S.a
[doc]
  a param

[code]
  a => 1 ~ preserve(parameter)
```
