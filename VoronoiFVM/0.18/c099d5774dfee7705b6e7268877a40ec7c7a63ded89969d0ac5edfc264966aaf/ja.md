```julia
scalarplot(
    sys::VoronoiFVM.AbstractSystem,
    sol::AbstractMatrix;
    species,
    kwargs...
) -> Any

```

解の1つの種をプロットします。
