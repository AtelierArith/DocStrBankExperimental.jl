```
@chkey a b c 123
```

Build a checkpointing key from the surrounding module and function names and the given arguments. This is intended for easy construction of checkpointing keys.

# Example

```julia
module MyModule

using Actors

function mykey()
    a = 1
    b = 2
    c = 3
    # do something
    return @chkey a b c 123
end

export mykey
end # MyModule

julia> using .MyModule

julia> mykey()
:MyModule_mykey_a_b_c_123
```
