```julia
get_subsystems(
    sys::PowerSystems.System
) -> Base.KeySet{String, Dict{String, Set{Base.UUID}}}

```

システム内のすべてのサブシステム名のイテレータを返します。
