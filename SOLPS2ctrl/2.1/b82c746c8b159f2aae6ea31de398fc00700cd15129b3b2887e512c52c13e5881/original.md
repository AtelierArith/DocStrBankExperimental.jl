```
geqdsk_to_imas!(
    eqdsk_file::String,
    dd::IMAS.dd;
    set_time::Union{Nothing, Float64}=nothing,
    time_index::Int=1,
)
```

Transfers the equilibrium reconstruction from an EFIT-style gEQDSK file into the IMAS DD structure.
