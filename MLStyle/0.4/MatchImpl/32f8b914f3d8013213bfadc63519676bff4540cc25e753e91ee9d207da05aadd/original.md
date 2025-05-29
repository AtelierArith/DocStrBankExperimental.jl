```
@trymatch <item> begin
    <pattern> => <result>
    <pattern> => <result>
end
```

Very similar to [`@match`](@ref), except that a failure to match does nothing instead of throwing a "match non-exhaustive" error.

It is equivalent to

```julia
@match <item> begin
    <pattern> => <result>
    <pattern> => <result>
    _ => nothing
    end
```
