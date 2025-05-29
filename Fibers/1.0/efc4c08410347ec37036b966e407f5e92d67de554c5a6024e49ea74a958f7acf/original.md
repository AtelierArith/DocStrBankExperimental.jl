```
Base.show(mri::MRI; plane::Char='a', z::Union{Int64, Nothing}=nothing, t::Union{Int64, Nothing}=nothing, title::Union{String, Nothing}=nothing)
```

Show the `z`-th slice from the `t`-th frame of an `MRI` structure, along the specified `plane` ('a': axial; 's': sagittal; 'c': coronal).
