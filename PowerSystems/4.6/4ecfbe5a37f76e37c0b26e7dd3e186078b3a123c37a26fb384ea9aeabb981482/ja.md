```julia
has_component(
    sys::PowerSystems.System,
    T::Type{<:PowerSystems.Component},
    name::AbstractString
) -> Bool

```

型Tのコンポーネントが名前で存在するかどうかを確認します。
