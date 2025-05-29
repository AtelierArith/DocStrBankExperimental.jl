```julia
remove_subsystem!(
    sys::PowerSystems.System,
    subsystem_name::AbstractString
)

```

システムからサブシステムを削除します。

サブシステム名が保存されていない場合はArgumentErrorをスローします。
