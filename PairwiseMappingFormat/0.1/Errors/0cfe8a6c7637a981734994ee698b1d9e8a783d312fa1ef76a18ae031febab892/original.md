```
module Errors
```

Wrapper module used to contain the instances of error types, and not pollute the namespace of the package.

# Examples

```jldoctest
julia> print(PAF.Errors.InvalidZero)
InvalidZero
```

See also: [`ParserException`](@ref)
