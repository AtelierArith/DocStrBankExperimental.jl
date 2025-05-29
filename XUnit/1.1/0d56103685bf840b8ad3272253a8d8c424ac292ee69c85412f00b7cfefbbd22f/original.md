```
runtests(args::Vector{String})
```

Include file `test/runtests.jl` and execute test sets matching the regular expressions in `args` (where a leading '-' or '¬' indicates that tests matching the expression should be excluded).

# Examples

```jldoctest
julia> runtests(["t/a/.*"])         # Run all tests under `t/a`

julia> runtests(["t/.*", "¬t/b/2"])  # Run all tests under `t` except `t/b/2`
```
