```
issuccess(code::ExitCode) -> Bool
```

Return `true` if this system exit code represents successful termination, `false` otherwise.

# Examples

```jldoctest
julia> issuccess(Sysexits.ok)
true

julia> issuccess(Sysexits.usage)
false
```
