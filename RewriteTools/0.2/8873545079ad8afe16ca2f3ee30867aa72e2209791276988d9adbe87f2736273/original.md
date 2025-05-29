```
@capture ex pattern
```

Uses a `Rule` object to capture an expression if it matches the `pattern`. Returns `true` and injects slot variable match results into the calling scope when the `pattern` matches, otherwise returns false. The rule language for specifying the `pattern` is the same in @capture as it is in `@rule`.

```julia
julia> @syms a; ex = a^a;

julia> if @capture ex (~x)^(~x)
           @show x
       elseif @capture ex 2(~y)
           @show y
       end;
x = a
```

See also: [`@rule`](@ref)
