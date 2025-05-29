```
get_timeslice(el_type::Type{Z}, @nospecialize(ids::IDS), time0::Float64=global_time(ids), scheme::Symbol=:constant; slice_pulse_schedule::Bool=false) where {Z<:Real}
```

get*timeslice that retuns IDS of type `el*type`
