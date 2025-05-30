```
isfailure(code::ExitCode) -> Bool
```

Return `true` if this system exit code represents unsuccessful termination, `false` otherwise.

# Examples

```jldoctest
julia> isfailure(Sysexits.ok)
false

julia> isfailure(Sysexits.usage)
true
```
