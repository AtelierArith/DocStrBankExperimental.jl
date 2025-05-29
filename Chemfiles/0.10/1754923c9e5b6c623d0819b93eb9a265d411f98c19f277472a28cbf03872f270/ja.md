```julia
set_property!(
    residue::Chemfiles.Residue,
    name::String,
    value::Union{Bool, Float64, String, Vector{Float64}}
)

```

指定された残基の名前付きプロパティを設定します。
