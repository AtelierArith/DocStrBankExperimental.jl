```
viewer(
    daf::DafReader;
    [name::Maybe{AbstractString} = nothing,
    axes::Maybe{ViewAxes} = nothing,
    data::Maybe{ViewData} = nothing]
)::DafReadOnly
```

Wrap `daf` data with a read-only [`DafView`](@ref). The exposed view is defined by a set of queries applied to the original data. These queries are evaluated only when data is actually accessed. Therefore, creating a view is a relatively cheap operation.

If the `name` is not specified, the result name will be based on the name of `daf`, with a `.view` suffix.

Queries are listed separately for axes and data.

!!! note
    As an optimization, calling `viewer` with all-empty (default) arguments returns a simple [`DafReadOnlyWrapper`](@ref), that is, it is equivalent to calling [`read_only`](@ref). Additionally, saying `data = ALL_DATA` will expose all the data using any of the exposed axes; you can write `data = [ALL_DATA..., key => nothing]` to hide specific data based on its `key`.

