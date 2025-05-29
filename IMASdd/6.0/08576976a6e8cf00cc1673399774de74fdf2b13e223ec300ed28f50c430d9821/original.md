```
copy_timeslice!(
    @nospecialize(ids0::IDS{T1}),
    @nospecialize(ids::IDS{T2}),
    time0::Float64,
    scheme::Symbol;
    slice_pulse_schedule::Bool) where {T1<:Real,T2<:Real}
```

Copy data at a given time from `ids` to `ids0`
