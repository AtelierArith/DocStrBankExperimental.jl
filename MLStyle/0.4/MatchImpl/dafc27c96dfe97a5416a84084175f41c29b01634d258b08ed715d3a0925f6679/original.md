```
@tryswitch <item> begin
    @case <pattern>
        <action>
end
```

Very similar to [`@switch`](@ref), except that a failure to match does nothing instead of throwing a "match non-exhaustive" error.

It is equivalent to

```julia
@switch <item> begin
    @case <pattern>
        <action>
    @case _
        nothing
    end
```
