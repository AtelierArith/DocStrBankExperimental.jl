```julia
set_name!(
    component::PowerSystems.Component,
    name::AbstractString
) -> AbstractString

```

コンポーネントの名前を設定します。

コンポーネントがシステムに接続されている場合は例外をスローします。
