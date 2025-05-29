```julia
set_property!(
    atom::Chemfiles.Atom,
    name::String,
    value::Union{Bool, Float64, String, Vector{Float64}}
)

```

指定された原子の名前付きプロパティを設定します。
