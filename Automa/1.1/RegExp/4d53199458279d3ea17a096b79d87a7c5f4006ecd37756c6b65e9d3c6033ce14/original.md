```
@re_str -> RE
```

Construct an Automa regex of type `RE` from a string. Note that due to Julia's raw string escaping rules, `re"\\"` means a single backslash, and so does `re"\\\\"`, while `re"\\\\\""` means a backslash, then a quote character.

Examples:

```julia
julia> re"ab?c*[def][^ghi]+" isa RE
true 
```

See also: [`RE`](@ref)
