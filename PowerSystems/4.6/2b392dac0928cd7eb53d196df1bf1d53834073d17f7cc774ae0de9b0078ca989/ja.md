```julia
remove_component!(
    _::Type{T<:PowerSystems.Component},
    sys::PowerSystems.System,
    name::AbstractString
)

```

システムから名前でコンポーネントを削除します。

コンポーネントが保存されていない場合はArgumentErrorをスローします。
