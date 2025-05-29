```
@bitflags [mutable] struct MyFlags
    flagA
    flagB
    _ # padding
    flagC
end
```

Construct a struct representing various boolean flags, stored in a compact format where each flag takes up a single bit. Field access gives a `Bool`, explicit padding can be declared by naming a field `_`. Field names (other than padding) need to be unique. The struct can optionally be marked `mutable`.

See also [`@bitfield`](@ref).

!!! warning "Struct size"
    Due to compiler limitations, the size of the resulting object will (currently) always be a multiple of 8 bits. The additional bits added due to this are considered padding and can not be relied on to exist. They may be removed in a future release without notice.


# Examples

```jldoctest
julia> @bitflags mutable struct MyFlags
           flagA
           flagB
           _ # padding
           flagC
       end

julia> flags = MyFlags(true, false, true)
MyFlags(flagA: true, flagB: false, flagC: true)

julia> flags.flagA
true

julia> flags.flagB
false

julia> flags.flagB = true
true

julia> flags.flagB
true

julia> sizeof(flags)
1
```
